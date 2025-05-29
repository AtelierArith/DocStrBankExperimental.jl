`Input1D`は、`probNFE`関数に渡す入力をラップするための構造体です。引数は以下の順序で指定されます。

# Input1D 引数

  * `α  :: AbstractFloat`
  * `v  :: AbstractFloat`
  * `V0 :: fV0`: 数値または関数であることができます
  * `L  :: Number`
  * `N  :: Integer`
  * `T  :: AbstractFloat`
  * `n  :: Integer`
  * `I  :: fI`: 外部入力関数
  * `K  :: fK`: 接続性関数
  * `S  :: fS`: 発火率関数

`I`、`K`、および`S`関数の宣言：

  * 関数Iは、引数を持たなければなりません: `I(x,t)`
  * 関数Kは、引数を持たなければなりません: `K(x)`
  * 関数Sは、引数を持たなければなりません: `S(V)`
