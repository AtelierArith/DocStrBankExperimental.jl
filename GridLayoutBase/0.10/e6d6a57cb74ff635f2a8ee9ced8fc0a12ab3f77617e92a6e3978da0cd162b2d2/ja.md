```
with_updates_suspended(f::Function, gl::GridLayout; update = true)
```

`gl` のレイアウト更新を無効にし、関数 `f` を呼び出します。`update` が true の場合、`f` が返った後にレイアウト更新を強制します。
