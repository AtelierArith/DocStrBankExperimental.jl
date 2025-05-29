function HGLET*GHWT*BestBasis_minrelerror(GP::GraphPart, G::GraphSig;     dmatrixH::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      dmatrixHrw::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixHsym::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),     dmatrixG::Array{Float64,3} = Array{Float64,3}(undef,0,0,0),      compare::Bool = true)

```
信号 'G' を近似するための最適基底を見つけるために、相対誤差を最小化しながらコスト関数として一連のタウ測定を用いた最適基底探索を行います
    (tau = 0.1,0.2,...,1.9)。
```

### 入力引数:

  * `dmatrixH`: HGLET展開係数の行列 ==> Lの固有ベクトル
  * `dmatrixHrw`: HGLET展開係数の行列 ==> Lrwの固有ベクトル
  * `dmatrixHsym`: HGLET展開係数の行列 ==> Lsymの固有ベクトル
  * `dmatrixG`: GHWT展開係数の行列
  * `GP`: GraphPartオブジェクト
  * `G`: GraphSigオブジェクト
  * `compare`: falseの場合、ハイブリッド最適基底をGHWTの細から粗への最適基底と比較しない

### 出力引数:

  * `dvec`: 最適基底に対応する展開係数のベクトル
  * `BS`: 最適基底を指定するBasisSpecオブジェクト
  * `trans`: 信号のその部分に使用された変換を指定します   00 = Lを用いたHGLET   01 = Lrwを用いたHGLET   10 = Lsymを用いたHGLET   11 = GHWT
  * `tau`: 最小の相対誤差をもたらすタウ
