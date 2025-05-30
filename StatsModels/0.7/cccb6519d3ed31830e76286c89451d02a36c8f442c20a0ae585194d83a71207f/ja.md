カテゴリ変数のコントラストコーディングシステムを記述するためのインターフェース。

`AbstractContrasts`の具体的なサブタイプは、カテゴリデータベクターを`ModelMatrix`の数値列に変換する特定の方法を記述します。各インスタンス化には、生成する列のレベルと基準レベルをオプションで含めることができます。指定されていない場合、これらは`ContrastsMatrix`が生成される際にデータから取得されます（`ModelFrame`の構築中）。

# コンストラクタ

`C <: AbstractContrast`の場合：

```julia
C()                                     # レベルは後で推測される
C(levels = ::Vector{Any})               # レベルは後でデータに対してチェックされる
C(base = ::Any)                         # 基準レベルを指定
C(levels = ::Vector{Any}, base = ::Any) # レベルと基準を指定
```

# 引数

  * `levels`: オプションで、データのレベルをここで指定できます。これにより、レベルの順序を指定できます。指定された場合、レベルは`ContrastsMatrix`が構築される際に実際にデータに存在するレベルと照合されます。ミスマッチがあるとエラーが発生します。データに存在しないレベルはモデル行列に空の列をもたらし、コントラストに存在しないレベルは空または未定義の行をもたらします。
  * `base`: 基準レベルも指定できます。これの実際の解釈は特定のコントラストタイプに依存しますが、一般的には「参照」レベルとして考えることができます。デフォルトでは最初のレベルになります。

# コントラストコーディングシステム

  * [`DummyCoding`](@ref) - 各非基準レベルを0-1インジケーター列としてコーディングします。
  * [`EffectsCoding`](@ref) - 各非基準レベルを1、基準を-1としてコーディングします。
  * [`HelmertCoding`](@ref) - 各非基準レベルを下位レベルの平均からの差としてコーディングします。
  * [`SeqDiffCoding`](@ref) - 変数の連続レベル間の差をコーディングします。
  * [`HypothesisCoding`](@ref) - 各レベルの平均応答の重み付けを与える仮説行列を介してコントラストを手動で指定します。
  * [`StatsModels.ContrastsCoding`](@ref) - モデル行列に直接コピーされるコントラスト行列を手動で指定します。

最後の2つのコーディングタイプ、`HypothesisCoding`と`StatsModels.ContrastsCoding`は、コントラスト行列を手動で指定する方法を提供します。`k`レベルの変数`x`に対して、コントラスト行列`M`は`k×k-1`行列であり、`k`レベルを`k-1`モデル行列列にマッピングします。具体的には、`X`を`x`のフルランクインジケータ行列とし、`X[i,j] = 1`は`x[i] == levels(x)[j]`の場合、そうでなければ0とします。次に、コントラスト行列`M`によって生成されるモデル行列列は`Y = X * M`です。

*仮説行列*は、生成されたコントラストの回帰係数によって表されるグループ平均応答の重み付けされた組み合わせを与える`k-1×k`行列です。コントラスト行列は仮説行列の一般化された擬似逆行列（例：`LinearAlgebra.pinv`）です。詳細については[`HypothesisCoding`](@ref)またはSchad et al. (2020)を参照してください。

# 拡張

カスタムコントラストを指定する最も簡単な方法は`HypothesisCoding`または`StatsModels.ContrastsCoding`を使用することです。しかし、実際にカスタムコントラストコーディングシステムを実装したい場合は、`AbstractContrasts`をサブタイプ化できます。これには、コンストラクタ、レベルから`ModelMatrix`列値へのマッピングを行う実際のコントラスト行列を構築するための`contrasts_matrix`メソッド、および（オプションで）`coefnames`メソッドが必要です：

```julia
mutable struct MyCoding <: AbstractContrasts
    ...
end

contrasts_matrix(C::MyCoding, baseind, n) = ...
coefnames(C::MyCoding, levels, baseind) = ...
```

# 参考文献

Schad, D. J., Vasishth, S., Hohenstein, S., & Kliegl, R. (2020). How to capitalize on a priori contrasts in linear (mixed) models: A tutorial. *Journal of Memory and Language, 110*, 104038. https://doi.org/10.1016/j.jml.2019.104038
