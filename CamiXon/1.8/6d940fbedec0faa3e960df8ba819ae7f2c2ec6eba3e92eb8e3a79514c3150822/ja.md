```
Def(T, atom, spinorbit, pot, scr, o1, o2, o3, pos, epn, k, am, matLD)
```

フィールドを持つ型:

  * `.atom::Atom`             : 原子オブジェクト
  * `.spinorbit::Spinorbit`    : スピン軌道オブジェクト
  * `.codata::Codata`           : コデータオブジェクト
  * `.pot::Vector{T}`        : 表形式のポテンシャル関数
  * `.scr::Vector{T}`        : 表形式のスクリーン関数
  * `.potscr::Vector{T}`        : 表形式のスクリーンされたポテンシャル関数
  * `.G::Vector{Matrix{T}}`: ゼロで埋められた行列のベクトル
  * `.σ::Vector{Matrix{T}}`: ゼロで埋められた行列のベクトル
  * `.Minv::Vector{Matrix{T}}`: ゼロで埋められた行列のベクトル
  * `.pos::Pos`              : フィールド Na, Nlctp, Nmin, Nuctp, Nb, N およびノードを持つオブジェクト
  * `.epn::Int`              : エンドポイントの数台形補正 - 奇数でなければならない
  * `.k::Int`              : アダムス-モールトンの次数
  * `.am::Vector{T}`        : アダムス-モールトンの重み係数
  * `.matLD::Matrix{T}`        : ラグランジュ微分行列

オブジェクト `Def` は、関数 [`castDef`](@ref) を使用して作成するのが最適です。
