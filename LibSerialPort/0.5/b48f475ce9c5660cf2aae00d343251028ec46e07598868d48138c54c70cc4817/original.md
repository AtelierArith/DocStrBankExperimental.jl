```
print_port_metadata(sp::SerialPort; show_config::Bool = true)
```

Print info found for this port. Note: port should be open to obtain a valid FD/handle before accessing fields.

`show_config` is `true` by default and prints out the current port settings.
