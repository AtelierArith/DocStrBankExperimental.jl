```
hvvendor()
```

Determine the hypervisor vendor as a Julia symbol or `:NoHypervisor` if not running a hypervisor. In case the hypervisor vendor identification is unknown `:Unknown` is returned (then also consider raising an issue on Github).
