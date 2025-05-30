```
inrelativeinterior(p::VRepElement, h::HRepElement)
```

`p`が`h`の相対内部にあるかどうかを返します。`h`が超平面である場合、`p in h`と同じです。なぜなら、超平面の相対内部はそれ自体だからです。`h`が半空間である場合、`ininterior(p, h)`と同じです。

```
inrelativeinterior(p::VRepElement, h::HRep)
```

`p`が`h`の相対内部にあるかどうかを返します。例えば、`h`を支持するすべての超平面と半空間の相対内部においてです。
