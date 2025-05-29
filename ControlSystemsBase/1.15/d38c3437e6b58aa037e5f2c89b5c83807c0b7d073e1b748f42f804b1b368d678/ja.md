```
fig = pzmap(fig, system, args...; hz = false, kwargs...)
```

`fig`のポールゼロマップを作成します。`LTISystem`(s)の`args`と`kwargs`は`scatter`プロットコマンドに送信されます。

離散システムのために描画される単位円をカスタマイズするには、ライン属性を変更します。例えば、`linecolor=:red`のようにします。

`hz`がtrueの場合、すべてのポールとゼロは1/2πでスケーリングされます。
