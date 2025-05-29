```
ininterior(p::VRepElement, h::HRepElement)
```

`p`が`h`の内部にあるかどうかを返します。`h`がハイパープレーンの場合、常に`false`を返します。`h`が半空間$\langle a, x \rangle \leq \beta$の場合、`p`が開半空間$\langle a, x \rangle < \beta$にあるかどうかを返します。

```
ininterior(p::VRepElement, h::HRep)
```

`p`が`h`の内部にあるかどうかを返します。例えば、`h`を支持するすべてのハイパープレーンと半空間の内部にあるかどうかです。
