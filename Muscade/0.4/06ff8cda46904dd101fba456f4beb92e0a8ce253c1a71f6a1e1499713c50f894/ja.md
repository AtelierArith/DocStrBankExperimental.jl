```
QuickFix <: AbstractElement
```

「1行」のコードでシンプルな要素を作成するための要素です。このように作成された要素にはいくつかの制限があります：

  * X-dofのみを持つ物理要素。
  * `R`のみが観測可能です。

この要素はテスト用に意図されています。Muscadeベースのアプリケーションは、これをAPIに含めるべきではありません。

# コンストラクタへの名前付き引数

  * `inod::NTuple{Nx,𝕫}`。X-dofの要素-ノード番号。
  * `field::NTuple{Nx,Symbol}`。X-dofのフィールド。
  * `res::Function`、ここで `res(X::ℝ1,X′::ℝ1,X″::ℝ1,t::ℝ) → ℝ1`、残差。

# 例

剛性2の1次元線形弾性スプリング。

```jldoctest; output = false
using Muscade
model = Model(:TestModel)
node1  = addnode!(model,𝕣[0])
node2  = addnode!(model,𝕣[1])
e = addelement!(model,QuickFix,[node1,node2];inod=(1,2),field=(:tx1,:tx1),
                res=(X,X′,X″,t)->Svector{2}(2*(X[1]-X[2]),2*(X[2]-X[1])) )

# output

Muscade.EleID(1, 1)                       
```
