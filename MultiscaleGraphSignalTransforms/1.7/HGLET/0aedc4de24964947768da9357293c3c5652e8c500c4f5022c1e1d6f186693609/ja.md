function HGLET_BestBasis(GP::GraphPart;      dmatrix::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     gltype::Symbol = :L, cfspec::Any = 0.1, flatten::Any = 1)

```
入力行列からHGLETの最適基底を選択します
```

### 入力引数

  * `GP`:      GraphPartオブジェクト
  * `dmatrix`: HGLET展開係数の行列
  * `gltype`:  HGLET辞書に使用されるグラフラプラシアン行列のタイプ   (デフォルト = :L)
  * `cfspec`: 使用するコスト関数仕様: 詳細はutils.jlを参照してください。 数字、例えばpの場合、l^pノルムが使用されます。 関数の場合、その関数が使用されます。 デフォルトは0.1、すなわちl^0.1です。
  * `flatten`: ベクトル値データをスカラー値データにフラット化する方法; 数字、例えばpの場合、l^pノルムの合計が計算されます。 :ash、:entropyなど、他にも多くのオプションがあります。 詳細はutils.jlを参照してください。 デフォルトは1、すなわち係数のl^1ノルムの合計です。

### 出力引数

  * `dvec`: 最適基底に対応する展開係数のベクトル
  * `BS`:   最適基底を指定するBasisSpecオブジェクト
