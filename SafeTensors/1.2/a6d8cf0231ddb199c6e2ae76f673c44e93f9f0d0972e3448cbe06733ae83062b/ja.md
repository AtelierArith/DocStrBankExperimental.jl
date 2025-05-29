```
load_sharded_safetensors(dir::AbstractString; mmap = true)
```

デフォルトのインデックスファイル `model.safetensors.index.json` が `dir` にあり、シャーディングされたテンソルをロードするために使用されます。
