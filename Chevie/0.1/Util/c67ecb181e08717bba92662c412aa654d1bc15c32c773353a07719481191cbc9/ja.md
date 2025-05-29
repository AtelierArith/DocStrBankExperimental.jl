`@forward T.f f1,f2,...`

は定義を委譲するマクロです。上記は次のように生成します。

```
f1(a::T,args...)=f1(a.f,args...)
f2(a::T,args...)=f2(a.f,args...)
...
```
