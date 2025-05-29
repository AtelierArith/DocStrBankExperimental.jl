compareModelObjects(mo1, mo2; tol=1.0e-15, verbose=false)

2つのモデルオブジェクトをフィールドごとに比較します。出力は(differences, max*abs*diff)の形式で、differencesは観測された違いを示すベクトルであり、max*abs*diffはすべてのフィールドにわたる違いの最大絶対値です。
