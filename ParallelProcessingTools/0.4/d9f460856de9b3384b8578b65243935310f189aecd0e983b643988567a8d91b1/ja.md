```
getlocalvalue(x::Any) = x
getlocalvalue(x::ThreadLocal) = x[]
```

プレーンな値とスレッドローカルな値に統一された方法でアクセスします。
