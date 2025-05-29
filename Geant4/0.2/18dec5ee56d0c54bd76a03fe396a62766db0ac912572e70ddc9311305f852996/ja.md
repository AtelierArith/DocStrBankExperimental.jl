```
G4JLScoringMesh(name, mesh; <キーワード引数>)
```

Geant4アプリケーションに追加するスコアリングメッシュを作成します。

# 引数

  * `name::String`: スコアリングメッシュの名前
  * `mesh::AbstractMesh`: メッシュインスタンス。`BoxMesh`または`CylinderMesh`のいずれか
  * `bins::Tuple`: x, y, zのビン数を含むタプル（デフォルトは30, 30, 30）
  * `translation::Tuple`: メッシュのワールドボリュームに対する位置 (x,y,z)。デフォルトは(0,0,0)。
  * `rotation::Tuple`: ワールドボリュームに対するメッシュの回転。デフォルトは(0,0,0)
  * `quantities::Vector`: スコアリングされる量のベクター（例: `energyDeposit`, `doseDeposit`, `nOfStep`）
