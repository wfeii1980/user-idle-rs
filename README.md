# Get the idle time of a user

| OS              | Supported |
| --------------- | --------- |
| Linux (x11)     | ✔️         |
| Linux (dbus)    | ✔️*        |
| Linux (wayland) | ❌         |
| Windows         | ✔️         |
| MacOS           | ✔️         |

\* DBus returns the time the session has been locked, not the time since the last user input event.

By default, x11 is used on Linux. DBus can be enabled in `Cargo.toml` by disabling default-features and enabling `dbus`.

### Example

```rust
use user_idle::UserIdle;

let idle = UserIdle::get_time().unwrap();

let idle_seconds = idle.as_seconds();
let idle_minutes = idle.as_minutes();
```
Check the [documentation](https://docs.rs/user-idle/latest/user_idle/) for more methods

### Cross compiling Linux platform `dbus` dependencies requires features `vendored`

```shell
cargo build --target i686-unknown-linux-gnu --no-default-features --features vendored
```
