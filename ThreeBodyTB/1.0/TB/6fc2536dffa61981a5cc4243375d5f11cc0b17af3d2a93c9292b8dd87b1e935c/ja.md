function Hk(h::tb*crys*kspace, kpoint)

k点でのバンド構造を `tb_crys_kspace` オブジェクトから計算します。注意、事前に計算された k 点のみを返すことができます。任意の k 点を取得するには、実空間バージョンが必要です。

#戻り値

  * `vect` - k点での固有ベクトル num*wan × num*wan 複素行列
  * `vals` - 固有値 (num_wan)
  * `hk` - k点でのハミルトニアン
  * `sk` - k点での重なり行列
  * `vals0` - <vect | Hk0 | vect> ここで Hk0 はハミルトニアンの非SCF部分です。

#引数

  * `h::tb_crys_kspace` - tb*crys*kspace オブジェクト
  * `kpoint` - 例: `[0.0,0.0,0.0]`
  * `scf=missing` - デフォルトは h から SCF を取得します。
