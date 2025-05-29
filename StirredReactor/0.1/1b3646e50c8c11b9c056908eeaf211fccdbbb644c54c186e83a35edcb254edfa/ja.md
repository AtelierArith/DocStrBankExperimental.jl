他のパッケージから呼び出すための関数で、主にリアクターネットワークモデリングを目的としています。

# 使用法

cstr(inlet*comp, T, p, time; Asv=1.0, chem, thermo*obj, md)

  * inlet_comp : リアクター入口での種とそのモル分率の辞書
  * T : 操作温度 (K)
  * p : 操作圧力 (Pa)
  * q : 体積流量 (m3/s)
  * time : 積分時間 (s)
  * AsV : 表面積対体積比 (表面反応の場合に重要。気相化学の場合は1)
  * thermo_obj : 種の熱力学オブジェクト (IdealGasパッケージのドキュメントを参照してください)
  * md : MechanismDefinition (ReactionCommonsのドキュメントを参照してください)
