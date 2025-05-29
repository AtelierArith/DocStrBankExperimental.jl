```
todevice(x)
```

Move data to device, only when gpu is enable with `enable_gpu`, basically equal `Flux.gpu`. Otherwise just `Flux.cpu`.
