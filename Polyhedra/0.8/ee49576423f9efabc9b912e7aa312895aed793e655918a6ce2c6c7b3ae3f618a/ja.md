```
inrelativeinterior(p::VRepElement, h::HRepElement; tol)
```

`p`が`h`の相対内部にあるかどうかを返します。`h`が超平面である場合、`p in h`と同等であり、超平面の相対内部はそれ自体だからです。`h`が半空間である場合、`ininterior(p, h)`と同等です。

```
inrelativeinterior(p::VRepElement, h::HRep; tol)
```

`p`が`h`の相対内部にあるかどうかを返します。例えば、`h`を支持するすべての超平面と半空間の相対内部においてです。
