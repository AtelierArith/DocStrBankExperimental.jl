`DataSet`を格納することに加えて、`DataModel`は関数`model(x,θ)`とその導関数`dmodel(x,θ)`も含んでおり、ここで`x`はデータのx値を、`θ`はモデルが依存するパラメータのベクトルを示します。重要なことに、`dmodel`はパラメータ`θ`に関するモデルの導関数を含んでおり、x値に関するものではありません。例えば

```julia
DS = DataSet([1,2,3,4], [4,5,6.5,7.8], [0.5,0.45,0.6,0.8])
model(x::Number, θ::AbstractVector{<:Number}) = θ[1] * x + θ[2]
DM = DataModel(DS, model)
```

モデルの出力が複数のコンポーネントを持つ場合（すなわち`ydim > 1`）、性能向上のために**StaticArrays.jl**を使用して静的ベクトルを出力するようにモデル関数を定義することが推奨されます。`ydim = 1`の場合、**InformationGeometry.jl**はモデルが1つのコンポーネントを持つベクトルではなく数値を出力することを期待します。対照的に、パラメータ構成`θ`は常にベクトルとして提供されなければなりません（たとえそれが単一のコンポーネントしか持たない場合でも）。

最大尤度パラメータの初期推定値は、オプションで`DataModel`にベクトルとして渡すことができます。

```julia
DM = DataModel(DS, model, [1.0,2.5])
```

最大尤度推定$\theta_\text{MLE}$の探索を含む`DataModel`プロセスの構築中に、複数のテストが実行されます。必要に応じて、最大尤度推定とその後のテストの両方を、コンストラクタの最後の引数に`true`を追加するか、対応するキーワード引数`SkipTests=false`または`SkipOptim=false`を使用することでスキップできます。

```julia
DM = DataModel(DS, model, [-Inf,π,1], true)
```

上記の例のように`DataModel`が構築されると、パラメータ`θ`に関するモデルの勾配（すなわちその「ヤコビ行列」）は自動微分を使用して計算されます。あるいは、ヤコビ行列の明示的な解析式を手動で指定することもできます。

```julia
using StaticArrays
function dmodel(x::Number, θ::AbstractVector{<:Number})
   @SMatrix [x  1.]     # ∂(model)/∂θ₁ と ∂(model)/∂θ₂
end
DM = DataModel(DS, model, dmodel)
```

ヤコビ行列の出力は、列が異なるコンポーネントの`θ`に関する偏微分に対応し、行が異なるコンポーネントの`x`での評価に対応する行列でなければなりません。再度、厳密には要求されませんが、静的行列の形でヤコビ行列を出力することは、全体的な性能にとって通常有益です。

初期推定値の後に、`DataModel`コンストラクタにパラメータ空間に対する（対数化された）事前分布を指定することも可能です。例えば：

```julia
using Distributions
Dist = MvNormal(ones(2), [1 0; 0 3.])
LogPriorFn(θ) = logpdf(Dist, θ)
DM = DataModel(DS, model, [1.0,2.5], LogPriorFn)
```

`DM`という名前の`DataModel`に含まれる`DataSet`は`Data(DM)`を介してアクセスでき、モデルとそのヤコビ行列はそれぞれ`Predictor(DM)`と`dPredictor(DM)`を介して使用できます。MLEとMLEでの対数尤度の値はそれぞれ`MLE(DM)`と`LogLikeMLE(DM)`を介してアクセスできます。対数化された事前分布は`LogPrior(DM)`を介してアクセスできます。
