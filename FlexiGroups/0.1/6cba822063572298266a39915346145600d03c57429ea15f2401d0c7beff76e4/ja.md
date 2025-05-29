```
groupmap([keyf=identity], mapf, X; [restype=Dictionary])
```

`map(mapf, group(keyf, X))`と似ていますが、より効率的です。`mapf`関数の制限されたセットをサポートしています：`length`、`first`/`last`、`only`、`rand`。
