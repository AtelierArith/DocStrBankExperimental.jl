```
@quickcheck [n=nexpr] expr (vartuple :: T) [...]
```

`expr` で表現された性質が型 `T` の変数 `vartuple...` に対して成り立つかどうかを確認します。複数の変数宣言を指定することができます。反例が見つかった場合は `false` を返し、そうでない場合は `true` を返します。`true` の結果はその性質の証明にはなりません。

`nexpr` は性質の真偽を調べるために使用される擬似乱数入力の数です。特別なケースには影響しないため、常にチェックされます。特別なケースのみをチェックするには、`nexpr` をゼロに設定できます。

反例の再現性のために、入力は固定されたシードで擬似的にランダムに選ばれます。確認したい性質についてより確実性を高めるために `@quickcheck` を複数回実行する代わりに、より大きな `n` で一度実行してください。

カスタムデータ型や組み込みデータ型のカスタム分布で `@quickcheck` を使用するには、`generate` と `specialcases` を参照してください。カスタム分布用のデータ型（例：`Range{T,a,b}`）はこのモジュールで事前定義されています。

## 例

Ints に対する `+` の結合性を確認します：

```jldoctest
julia> @quickcheck (a+b == b+a) (a :: Int) (b :: Int)
true
```

別の構文とより多くのテスト数を用いた同じテスト：

```jldoctest
julia> @quickcheck n=10^6 (a+b == b+a) ((a, b) :: Int)
true
```

一方で、倍精度浮動小数点数の結合性のテストは失敗します。有限値のみが許可されている場合でも（`NaN`、±`Inf` はなし）：

```jldoctest
julia> @quickcheck (a+(b+c) == (a+b)+c || !all(isfinite, (a,b,c))) ((a,b,c) :: Float64)
┌ Warning: Property `a + (b + c) == (a + b) + c || (any(isnan, (a, b, c)) || any(isinf, (a, b, c)))` does not hold for (a = 0.3333333333333333, b = 1.0, c = 1.0).
└ @ RandomizedPropertyTest ~/store/zeug/public/RandomizedPropertyTest/src/RandomizedPropertyTest.jl:119
false
```

1周期にわたる `sin` の加法定理をテストします：

```jldoctest
julia> @quickcheck (sin(α - β) ≈ sin(α) * cos(β) - cos(α) * sin(β)) ((α, β) :: Range{Float64, 0, 2π})
true
```
