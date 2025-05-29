```
write(hid_device, data::Vector{UInt8})
```

`data`を`hid_device`にhidメッセージとして書き込みます。通常は64バイトです。
