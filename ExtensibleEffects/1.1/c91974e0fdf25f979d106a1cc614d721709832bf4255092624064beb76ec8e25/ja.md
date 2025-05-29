```
@syntax_eff begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end
```

拡張可能な効果の構文です。これは、`@pure`で前置されていないすべての値に`effect`を適用し、それらを`Eff`モナドに持ち上げます。結果は、それぞれの`Eff`モナド上で`@syntax_flatmap`を使用して結合され、最終的に`autorun`アルゴリズムを使用して実行されます。

## 例

```julia
autohandled_eff = @syntax_eff begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end

mycustomwrapper(i::Int) = collect(1:i)
# モナディックな構文を使用して、未処理の効果を解釈する前にラッパーを適用します
autohandled_eff = @syntax_eff mycustomwrapper begin
  a = [1,2,3]
  b = [a, a*a]
  @pure a, b
end
```

## インターフェース

新しい型のサポートを追加したい場合は、次のインターフェースを提供する必要があります：（Vectorはあくまで例です）

|                                                                      core function |                                                                                                                                                                                                                        description |
| ----------------------------------------------------------------------------------:| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| `ExtensibleEffects.eff_applies(handler::Type{<:Vector}, effectful::Vector) = true` |                                                                                                                                                                                  ハンドラーが適用される値を指定します（ハンドラーVectorはもちろんVectorに適用されます） |
|             `ExtensibleEffects.eff_pure(handler::Type{<:Vector}, value) = [value]` |                                                                                                                                                                                                プレーンな値をハンドラーのモナド、ここではVectorにラップします。 |
|                   `ExtensibleEffects.eff_flatmap(continuation, effectful::Vector)` | 現在の効果に継続を適用します（ここでもVectorを例にしています）。プレーンな`TypeClasses.flatmap`との主な違いは、`continuation`がプレーンな`Vector`を返さず、`Eff{Vector}`を返すことです。この`continuation`をプレーンな`map`で適用すると、`Vector{Eff{Vector}}`になります。しかし、`eff_flatmap`は`Eff{Vector}`を返す必要があります。 |
