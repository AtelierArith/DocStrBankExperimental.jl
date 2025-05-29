```
dr = resample(d::InputOutputData, f)
```

iddata `d` を分数 `f` で再サンプリングします。例えば、`f = fs_new / fs_original` のように。
