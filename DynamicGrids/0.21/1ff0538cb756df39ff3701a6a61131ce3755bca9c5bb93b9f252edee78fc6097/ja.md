```
Aux <: ParameterSource

Aux{K}()
Aux(K::Symbol)
```

キー `K` を持つ補助配列をパラメータソースとして使用します。

ルールで実装されているのは次の通りです：

```julia
get(data, rule.myparam, I)
```

`Aux` パラメータがルール構築時に指定されると：

```julia
rule = SomeRule(; myparam=Aux{:myaux})
output = ArrayOutput(init; aux=(myaux=myauxarray,))
```

配列が DimensionalData.jl の `DimArray` で `Ti`（時間）次元を持つ場合、正しい間隔が自動的に選択され、各タイムステップのために事前計算されるため、重大なオーバーヘッドはありません。

現在、これはデフォルトでサイクルされています。シミュレーションのタイムステップ（例：`Week`）が時間次元の長さ（例：`Year`）に均等に収まらない場合、サイクリングが不正確である可能性があることに注意してください。これは、将来的にこの問題を修正するために DimensionalData.jl に `Cyclic` インデックスモードが必要になります。
