function HGLET*GHWT*BestBasis(GP::GraphPart;      dmatrixH::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixHrw::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      dmatrixHsym::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixG::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      cfspec::Any = 0.1,flatten::Any = 1)

```
複数の展開係数行列から最適な基底を選択します
```

### 入力引数

  * `dmatrixH`:    HGLET展開係数の行列 ==> Lの固有ベクトル
  * `dmatrixHrw`:  HGLET展開係数の行列 ==> Lrwの固有ベクトル
  * `dmatrixHsym`: HGLET展開係数の行列 ==> Lsymの固有ベクトル
  * `dmatrixG`:    GHWT展開係数の行列
  * `GP`:          GraphPartオブジェクト
  * `cfspec`: 使用するコスト関数の仕様: 詳細はutils.jlを参照してください。数値pの場合、l^pノルムが使用されます。関数の場合、その関数が使用されます。デフォルトは0.1、すなわちl^0.1です。
  * `flatten`: ベクトル値データをスカラー値データにフラット化する方法; 数値pの場合、l^pノルムの合計が計算されます。他にも多くのオプションがあります。:ash、:entropyなど。詳細はutils.jlを参照してください。デフォルトは1、すなわち係数のl^1ノルムの合計です。

### 出力引数

  * `dvec`:     最適基底に対応する展開係数のベクトル
  * `BS`:       最適基底を指定するBasisSpecオブジェクト
  * `trans`:    信号のその部分に使用された変換を指定します:   00 = Lを用いたHGLET   01 = Lrwを用いたHGLET   10 = Lsymを用いたHGLET   11 = GHWT
