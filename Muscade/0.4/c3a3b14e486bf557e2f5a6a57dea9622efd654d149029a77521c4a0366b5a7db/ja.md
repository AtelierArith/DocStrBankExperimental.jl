```
ElementCost{Teleobj,Treq,Tcost,Tcostargs} <: AbstractElement
```

別の「ターゲット」要素の自由度（dofs）と要素結果にコストを適用するための要素です。ターゲット要素はモデルに別途追加されてはなりません。代わりに、`ElementType`とターゲット要素への名前付き引数が`ElementCost`コンストラクタへの入力として提供されます。

# コンストラクタへの名前付き引数

  * `req`                 ターゲット要素から抽出される要素結果のリクエスト、[`@request`](@ref)を参照してください。                       リクエストはターゲット要素に直接宛てられるかのように構成されます（`eleres`での「プレフィックス」は不要です、「リクエスト可能な内部変数」を参照）。
  * `cost`                コスト関数 `cost(eleres,X,U,A,t,costargs...)→ℝ`                       `X`と`U`はタプル（自由度の導関数など）であり、`∂0(X)`,`∂1(X)`,`∂2(X)`                        は`cost`によって`X`（および`U`）の値と導関数にアクセスするために使用されなければなりません。                       `X`、`U`、および`A`は要素`ElementType`の自由度です。
  * `costargs=(;)`        コスト関数への追加引数の名前付きタプル
  * `ElementType`         関連する要素のコンストラクタの名前
  * `elementkwargs`       `ElementType`コンストラクタの名前付き引数を含む名前付きタプル。

# リクエスト可能な内部変数

`ElementConstraint`からリクエストできるもの

  * `cost`               コストの値

ターゲット要素からリクエストできるもの

  * `eleres(...)`        `...`はターゲット要素からのリクエスト可能なリストです。混乱を避けるために                       `eleres`で「プレフィックス」を付ける必要があります。

# 例

```
@once cost(eleres,X,U,A,t) = eleres.Fh^2
ele1 = addelement!(model,ElementCost,[nod1];req=@request(Fh),
                   cost=cost,ElementType=AnchorLine,
                   elementkwargs=(Λₘtop=[5.,0,0], xₘbot=[250.,0], L=290., buoyancy=-5e3))
```

参照: [`SingleDofCost`](@ref)、[`DofCost`](@ref)、[`@request`](@ref) 
