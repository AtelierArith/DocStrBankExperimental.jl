```
MeasurementModel
```

`MeasurementModel`は、相関した不確実性を持つベクトル入力のベクトル関数を表す抽象型です。`MeasurementModel`は、入力値で評価されたベクトル関数の出力と関連するヤコビ行列を計算する責任があります。

MeasurementModelが、入力値を表すUncertainValuesオブジェクトを受け取り、出力値を表すUncertainValuesオブジェクトを返すベクトル関数を表すことを強調するために、関数演算子がオーバーロードされています：

```
(mm::MeasurementModel)(uvs::UncertainValues)::UncertainValues
```

または

```
(mm::MeasurementModel)(uvs::Dict{<:Label, UncertainValue})::UncertainValues
```

これにより、MeasurementModelをUncertainValuesの関数として考えることができます。

さらに、`MeasurementModel`を組み合わせて、∘演算子を使用してマルチステップ計算を実装することができます。`mm1`と`mm2`が`MeasurementModel`であり、`mm2`の入力が`mm1`（および元の入力）から来る場合：

```
(mm2 ∘ mm1)(inputs) = mm2(mm1(inputs))
```

同様に、`mm3`と`mm4`が同じ入力を受け取る場合、次のように並行して計算できます：

```
(mm3 | mm4)(inputs) = cat(mm3(inputs), mm4(inputs))
```

`∘`と`|`を次のように組み合わせることができます：

```
(mm2 ∘ (mm3 | mm4) ∘ mm1)(inputs) = mm2(cat(mm3(mm1(inputs)),mm4(mm1(inputs))))
```

これは、最初に`o1=mm1(inputs)`を計算し、次に`o3=mm3(inputs+o1)`と`o4=mm4(inputs+o1)`を計算し、最後に`mm2(inputs+o1+o3+o4)`を計算します。

`MeasurementModel`を組み合わせることが魔法が起こるところです。複雑な測定モデルの場合、部分導関数の解析形式を計算することは実現不可能な場合があります。しかし、モデルを解析部分導関数を計算できる一連の小さな組み合わせ可能なステップに分解できる場合、ステップを組み合わせて完全なモデルを構築できます。もちろん、これは魔法ではなく、ヤコビ行列のこの特性から生じます：

$$
\mathbf{J}_{g(f(x))} |_x = \mathbf{J}_g(y) |_{f(x)} \mathbf{J}_{f(x)} |_x
$$

このフレームワークを測定モデルで使用するには、`YourMeasurementModel`のために`compute(...)`関数を実装する必要があります。

```
compute(mm::YourMeasurementModel, inputs::LabeledValues, withJac::Boolean)::MMResult
```

ここで

```
MMResult = Tuple{LabeledValues, Union{Missing,AbstractMatrix{Float64}}}
```

`compute(...)`関数は、モデルの出力値と入力値に対する出力値のヤコビ行列を計算する責任があります。ヤコビ行列は、出力値ごとに1行、入力値ごとに1列を持つ行列です。r,c-th要素の内容は、c-th入力値に対するr-th出力値の部分導関数です。

`MMResult`は、関数の出力値（`LabeledValues`）とヤコビ行列を`AbstractMatrix{Float64}`として表します。ベクトル値関数を単に計算するために`compute(...)`関数を最適化するために、ヤコビ行列は`withJac=true`のときのみ計算する必要があります。`withJac=false`の場合、ヤコビ行列に対して'missing'を返すことが推奨されます。これは、モンテカルロ伝播（`mcpropagate(...)`を使用）などの状況で、ヤコビ行列を計算するのが無駄であるが、関数値を計算するために同一のコードを使用したい場合に効率を促進します。
