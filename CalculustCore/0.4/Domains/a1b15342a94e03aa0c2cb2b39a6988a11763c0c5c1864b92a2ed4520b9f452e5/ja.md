```julia
deform(domain; ...)
deform(domain, mapping; isseparable, isrescaling)

```

`mapping`を介して`domain`を変形します。この関数のシグネチャは次のようになります。

```
mapping(r1, ..., rD) = x1, ..., xD
```

入力と出力は`NTuple{D, <:AbstractArray}`です。

# キーワード引数

  * `isrescaling` - `mapping`が再スケーリング操作である場合は`true`に設定します。すなわち、

    x1 = a1 + λ1 × x1(r1),

    ...,

    xD = aD + λD × xD(rD)
  * `isseparable` - `mapping`が分離可能である場合は`true`に設定します。すなわち、

    x1 = x1(r1),

    ...,

    xD = xD(rD)

TODO - AffineMap、LinearMap、SeparableMap、Transation、Rotationの型を作成する TODO - コンストラクタで`static_hasmethod`を確認する
