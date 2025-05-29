他のパッケージから呼び出すための関数で、主にリアクターネットワークモデリングを目的としています。

# メソッド-3

plug(inlet*comp, T, p, vel, l; chem, thermo*obj, md, geometry)

  * inlet*comp : 種類名とモル分率の辞書。気相化学の場合、inlet*compには入口に存在する種のみが含まれる場合があります。
  * T : 温度（K）
  * p : 圧力（Pa）
  * vel : 入口速度（m/s）
  * l : リアクターの長さ（m）
  * chem: 呼び出す化学反応: tuple Chemistry(surfchem, , true, user_defined)
  * thermo_obj : 熱力学オブジェクト
  * md : メカニズム定義（SurfaceReactions.jlおよびGaを参照してください）
  * geometry : リアクターの幾何学のタプル（dia,cat_geom）

      * dia: リアクターの直径
      * cat_geom : 触媒の幾何学的効果による反応速度の増強係数
