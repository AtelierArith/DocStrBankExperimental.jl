```julia
guess_from_hopf(
    br,
    ind_hopf,
    eigsolver,
    M,
    amplitude;
    phase
)

```

この関数は、Hopf分岐点に関するいくつかの有用な量を返します。より正確には、次のものを返します：

  * Hopf分岐が発生するパラメータ値
  * 分岐した周期軌道の周期
  * 分岐した周期軌道の推定値
  * Hopf分岐点での平衡点
  * Hopf分岐点での固有ベクトル

引数は次の通りです：

  * `br`: Hopf分岐点をリストする継続ブランチ
  * `ind_hopf`: `br.specialpoint`のような分岐ブランチのインデックス
  * `eigsolver`: 固有ベクトルを見つけるために使用される固有ソルバー
  * `M`: 周期軌道の推定における時間スライスの数
  * `amplitude`: 周期軌道の推定の振幅
