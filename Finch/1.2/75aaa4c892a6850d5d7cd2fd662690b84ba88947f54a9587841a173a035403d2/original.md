```
transfer(device, arr)
```

If the array is not on the given device, it creates a new version of this array on that device and copies the data in to it, according to the `device` trait. If the device is simply a data buffer, we copy the array into the buffer.
