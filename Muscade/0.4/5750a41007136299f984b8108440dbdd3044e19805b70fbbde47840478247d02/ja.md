```
ElementConstraint{Teleobj,λinod,λfield,Nu,Treq,Tg,Tgargs,Tmode} <: AbstractElement
```

他の「ターゲット」要素の要素結果に対して最適化の等式/不等式制約を適用するための要素です。ターゲット要素はモデルに別途追加されてはなりません。代わりに、`ElementType`とターゲット要素への名前付き引数が`ElementConstraint`コンストラクタへの入力として提供されます。

この要素は時間変化する最適化制約を生成します。例えば、すべての時間において、要素結果のフォン・ミーゼス応力が与えられた値を超えないようにするための`A`パラメータを見つけます。

この最適化制約によって導入されるラグランジュ乗数はクラス:Uです。

# コンストラクタへの名前付き引数

  * `λinod::𝕫`            ラグランジュ乗数の要素ノード番号。
  * `λfield::Symbol`      ラグランジュ乗数のフィールド。
  * `req`                 ターゲット要素から抽出される要素結果のリクエスト、[`@request`](@ref)を参照。                       リクエストはターゲット要素に直接アドレスされるかのように形成されます（`eleres`での「プレフィックス」は不要、内部変数のリクエストを参照）。
  * `gₛ::𝕣=1.`             ギャップのスケール。
  * `λₛ::𝕣=1.`             ラグランジュ乗数のスケール。
  * `gap`                 ギャップ関数 `gap(eleres,X,U,A,t,gargs...)→ℝ`                       `X`と`U`はタプル（自由度の導関数など）であり、`∂0(X)`,`∂1(X)`,`∂2(X)`                        は`cost`によって`X`（および`U`）の値と導関数にアクセスするために使用されます。                       `X`、`U`、および`A`は要素`ElementType`の自由度です。
  * `gargs::NTuple`       ギャップ関数への追加入力。
  * `mode::Function`      `mode(t::ℝ) -> Symbol`、値は任意の時点で`:equal`、                        `:positive`または`:off`です。`:off`制約は                        ラグランジュ乗数をゼロに設定します。
  * `ElementType`         関連する要素のコンストラクタの名前。
  * `elementkwargs`       `ElementType`コンストラクタの名前付き引数を含む名前付きタプル。

# リクエスト可能な内部変数

`ElementConstraint`からリクエストできるもの

  * `λ`                   制約のラグランジュ乗数。
  * `gap`                 制約のギャップ関数。

ターゲット要素からリクエストできるもの

  * `eleres(...)`         `...`はターゲット要素からのリクエスト可能なリストです。 それは`eleres`で「プレフィックス」される必要があります。そうしないと、`ElementConstraint`からリクエスト可能な変数との混乱を防ぐことができません。

δX

# 例

```
@once gap(eleres,X,U,A,t) = eleres.Fh^2
ele1 = addelement!(model,ElementCoonstraint,[nod1];req=@request(Fh),
                   gap,λinod=1,λfield=:λ,mode=equal, 
                   ElementType=AnchorLine,
                   elementkwargs=(Δxₘtop=[5.,0,0], xₘbot=[250.,0],L=290., buoyancy=-5e3))
```

参照: [`Hold`](@ref), [`DofConstraint`](@ref), [`off`](@ref), [`equal`](@ref), [`positive`](@ref), [`@request`](@ref)
