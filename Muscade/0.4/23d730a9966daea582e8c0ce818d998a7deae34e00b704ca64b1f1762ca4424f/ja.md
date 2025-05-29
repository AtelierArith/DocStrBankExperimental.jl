```
DofConstraint{λclass,Nx,Nu,Na,xinod,xfield,uinod,ufield,ainod,
    afield,λinod,λfield,Tg,Tmode} <: AbstractElement
```

物理/最適化の等式/不等式制約をdofに適用するための要素です。

制約はホロノミックであり、関与するdofの値に適用され、時間微分には適用されません。この要素は非常に一般的ですが、構築するのはあまりユーザーフレンドリーではありません。使いやすさを向上させるためにファクトリ関数が提供されています。符号の慣例は、ギャップ `g≥0` およびラグランジュ乗数 `λ≥0` です。

この要素は、入力引数 `λclass` に応じて3つのクラスの制約を生成できます。

  * `λclass=:X` 物理的制約。力学において、ラグランジュ乗数dofはギャップの双対である一般化された力です。ギャップ関数は `gap(x,t,gargs...)` の形式でなければなりません。
  * `λclass=:U 時間変化する最適化制約。例えば、すべての時間において応答が与えられた基準を超えないようにするための`A`-パラメータを見つけます。ギャップ関数は`gap(x,u,a,t,gargs...)` の形式でなければなりません。
  * `λclass=:A 時間不変の最適化制約。例えば、`A[1]+A[2]=gargs.somevalue`となるような`A`-パラメータを見つけます。ギャップ関数は`gap(a,gargs...)` の形式でなければなりません。

# コンストラクタへの名前付き引数

  * `xinod::NTuple{Nx,𝕫}=()`       制約される各X-dofの要素ノード番号。
  * `xfield::NTuple{Nx,Symbol}=()` 制約される各X-dofのフィールド。
  * `uinod::NTuple{Nu,𝕫}=()`       制約される各U-dofの要素ノード番号。
  * `ufield::NTuple{Nu,Symbol}=()` 制約される各U-dofのフィールド。
  * `ainod::NTuple{Na,𝕫}=()`       制約される各A-dofの要素ノード番号。
  * `afield::NTuple{Na,Symbol}=()` 制約される各A-dofのフィールド。
  * `λinod::𝕫`                     ラグランジュ乗数の要素ノード番号。
  * `λclass::Symbol`               ラグランジュ乗数のクラス（`:X`,`:U` または `:A`）。                                 制約のクラスについての説明を参照してください。
  * `λfield::Symbol`               ラグランジュ乗数のフィールド。
  * `gap::Function`                ギャップ関数。
  * `gargs::NTuple`                ギャップ関数への追加入力。
  * `mode::Function`               `mode(t::ℝ) -> Symbol` の形式で、任意の時点で `:equal`、                                 `:positive` または `:off` の値を持ちます。 `:off` 制約は                                 ラグランジュ乗数をゼロに設定します。

# 例

```jldoctest; output = false
using Muscade
model           = Model(:TestModel)
n1              = addnode!(model,𝕣[0]) 
e1              = addelement!(model,DofConstraint,[n1],xinod=(1,),xfield=(:t1,),
                              λinod=1, λclass=:X, λfield=:λ1,gap=(x,t)->x[1]+.1,
                              mode=positive)
e2              = addelement!(model,QuickFix  ,[n1],inod=(1,),field=(:t1,),
                              res=(x,u,a,t)->0.4x.+.08+.5x.^2)
initialstate    = initialize!(model)
setdof!(initialstate,1.;field=:λ1)
state           = solve(SweepX{0};initialstate,time=[0.],verbose=false) 
X               = state[1].X[1]

# 出力

2-element Vector{Float64}:
 -0.09999152289496528
  0.04500254313151041
```

参照: [`Hold`](@ref), [`ElementConstraint`](@ref), [`off`](@ref), [`equal`](@ref), [`positive`](@ref)
