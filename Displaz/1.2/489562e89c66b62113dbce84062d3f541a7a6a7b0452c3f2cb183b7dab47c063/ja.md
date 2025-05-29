```
viewplot([plotobj::DisplazWindow=current()];
         center=point_or_label, radius=dist_from_center, rotation=rot_matrix)
```

3Dカメラの視点を設定します。カメラモデルは、指定された回転の`center`でオブジェクトを表示するように設計されており、その位置を中心に回転します。

指定されていない場合、`plotobj`は現在のプロットウィンドウです。キーワード引数はカメラビューを次のように定義します：

  * `center`引数は3Dポイントまたはデータセットのラベルである場合があります。ラベルが指定された場合、関連するデータセットの重心が使用されます。
  * `radius`引数は、カメラが回転の中心からどれだけ離れているかを示す数値である必要があります。
  * `rotation`引数は、カメラがシーンをどの角度で見るかを指定します。これは、ポイントを標準のOpenGLカメラ座標（+x 右、+y 上、-z シーン内）に変換する行列である場合があります。あるいは、度数法でのタプル`(yaw, pitch, roll)`を指定することもでき、これは`Rotations.jl`の回転行列`RotZXZ(deg2rad(roll), deg2rad(pitch-90), deg2rad(yaw))`を使用するのと同等です。
