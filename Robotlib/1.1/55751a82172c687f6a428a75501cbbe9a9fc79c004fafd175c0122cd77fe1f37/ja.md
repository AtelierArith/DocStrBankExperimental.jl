この関数を、ロボットの運動学関数を取得したい文字列で実行します。例えば、`get_kinematic_functions("YuMi")`のようにします。現在、YuMiとABB IRB7600をサポートしています。返されるのは`fkine(q), ikine(T,q0), jacobian(q)`です。TODO: YuMi*left、Yumi*right Tbase*ikinePOEを実装する。
