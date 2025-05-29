```
hypervised()
```

Check whether the CPU reports to run a hypervisor context, that is, whether the current process runs in a virtual machine.

A positive answer may indicate that other information reported by the CPU is fake, such as number of physical and logical cores.  This is because the hypervisor is free to decide which information to pass.
