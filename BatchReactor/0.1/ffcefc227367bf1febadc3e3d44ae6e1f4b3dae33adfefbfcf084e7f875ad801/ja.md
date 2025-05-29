他のパッケージから呼び出すための関数で、主にリアクターネットワークモデリングを目的としています。

# 使用法

batch*reactor(inlet*comp, T, p, time; Asv=1.0, chem, thermo_obj, md)

  * inlet_comp : リアクター入口での種とそのモル分率の辞書
  * T : 動作温度 (K)
  * p : 動作圧力 (Pa)
  * time : 積分時間 (s)
  * Asv : 体積に対する表面積比 (表面反応の場合に重要。気相化学の場合は1)
  * thermo_obj : 種の熱力学オブジェクト (IdealGasパッケージのドキュメントを参照してください)
  * md : MechanismDefinition (ReactionCommonsのドキュメントを参照してください)
