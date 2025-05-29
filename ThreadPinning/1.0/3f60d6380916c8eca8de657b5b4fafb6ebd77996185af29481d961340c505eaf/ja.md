```
getnumanode(; threadid = nothing)
```

呼び出しスレッドが現在実行中のCPUスレッドに対応するNUMAノードのID（ゼロから始まる）を返します。呼び出しスレッドとは異なるJuliaスレッドを考慮するために`threadid`を指定することができます。
