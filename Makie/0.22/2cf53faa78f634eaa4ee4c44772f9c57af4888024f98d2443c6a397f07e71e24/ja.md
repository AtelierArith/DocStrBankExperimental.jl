```
Camera3D(scene[; kwargs...])
```

3Dカメラをマウスとキーボードのコントロールでセットアップします。

カメラの動作は、キーワード引数またはフィールド `settings` と `controls` を介して調整できます。

## 設定

設定には、マウスやキーボードのボタン以外のすべてが含まれます。

  * `projectiontype = Perspective` は投影のタイプを設定します。`Orthographic` または `Perspective` にできます。
  * `rotation_center = :lookat` はカメラの回転のデフォルトの中心を設定します。現在は `:lookat` または `:eyeposition` が許可されています。
  * `fixed_axis = true`: true の場合、パンはカメラの上方向ではなく (世界/プロット) z軸を使用します。
  * `zoom_shift_lookat = true`: true の場合、ズーム時にカーソルの下のデータを保持します。
  * `cad = false`: true の場合、オフセンターでズームするときに `lookat` の周りでビューを回転させます。
  * `clipping_mode = :adaptive`: `near` と `far` の処理方法を制御します。オプション:

      * `:static` は `near` と `far` をそのまま渡します
      * `:adaptive` は `near` を `norm(eyeposition - lookat)` でスケーリングし、`far` をそのまま渡します
      * `:view_relative` は `near` と `far` を `norm(eyeposition - lookat)` でスケーリングします
      * `:bbox_relative` は `near` と `far` をカメラに `update_cam!(..., bbox)` で渡されたシーンのバウンディングボックスにスケーリングします。 (より具体的には `far = 1` はバウンディングスフィアの最も遠い点にスケーリングされ、`near` は一般的に最も近い点に上書きされます。)
  * `center = true`: 新しいプロットが追加されたときに `center!(scene)` を呼び出すときにカメラの配置がリセットされるかどうかを制御します。
  * `keyboard_rotationspeed = 1.0` はキーボードベースの回転の速度を設定します。
  * `keyboard_translationspeed = 0.5` はキーボードベースの移動の速度を設定します。
  * `keyboard_zoomspeed = 1.0` はキーボードベースのズームの速度を設定します。
  * `mouse_rotationspeed = 1.0` はマウスの回転の速度を設定します。
  * `mouse_translationspeed = 0.5` はマウスの移動の速度を設定します。
  * `mouse_zoomspeed = 1.0` はマウスのズームの速度を設定します (マウスホイール)。
  * `circular_rotation = (false, false, false)` は (固定 x, 固定 y, 固定 z) 回転軸のための円形回転を有効にします。 (これは、マウスでシーンの中心の周りに円を描くと、連続的な回転が得られることを意味します。)

## コントロール

コントロールには、あらゆる種類のホットキー設定が含まれます。

  * `up_key   = Keyboard.r` は画面の上部に向かう移動のためのキーを設定します。
  * `down_key = Keyboard.f` は画面の下部に向かう移動のためのキーを設定します。
  * `left_key  = Keyboard.a` は画面の左側に向かう移動のためのキーを設定します。
  * `right_key = Keyboard.d` は画面の右側に向かう移動のためのキーを設定します。
  * `forward_key  = Keyboard.w` は画面に向かう移動のためのキーを設定します。
  * `backward_key = Keyboard.s` は画面から出る移動のためのキーを設定します。
  * `zoom_in_key   = Keyboard.u` はシーンにズームインするためのキーを設定します (視点を `lookat` に向かって移動)。
  * `zoom_out_key  = Keyboard.o` はシーンからズームアウトするためのキーを設定します (視点を `lookat` から離れて移動)。
  * `increase_fov_key = Keyboard.b` は視野を広げるためのキーを設定します。
  * `decrease_fov_key = Keyboard.n` は視野を狭めるためのキーを設定します。
  * `pan_left_key  = Keyboard.j` は画面の垂直軸の周りの回転のためのキーを設定します。
  * `pan_right_key = Keyboard.l` は画面の垂直軸の周りの回転のためのキーを設定します。
  * `tilt_up_key   = Keyboard.i` は画面の水平軸の周りの回転のためのキーを設定します。
  * `tilt_down_key = Keyboard.k` は画面の水平軸の周りの回転のためのキーを設定します。
  * `roll_clockwise_key        = Keyboard.e` は画面の回転のためのキーを設定します。
  * `roll_counterclockwise_key = Keyboard.q` は画面の回転のためのキーを設定します。
  * `fix_x_key = Keyboard.x` は (世界/プロット) x軸に対して移動と回転を固定するためのキーを設定します。
  * `fix_y_key = Keyboard.y` は (世界/プロット) y軸に対して移動と回転を固定するためのキーを設定します。
  * `fix_z_key = Keyboard.z` は (世界/プロット) z軸に対して移動と回転を固定するためのキーを設定します。
  * `reset = Keyboard.left_control & Mouse.left` はカメラをリセットするためのキーを設定します。これは `center!(scene)` を呼び出すのと同等です。
  * `reposition_button = Keyboard.left_alt & Mouse.left` はプロットオブジェクトにカメラを焦点を合わせるためのキーを設定します。
  * `translation_button = Mouse.right` はドラッグ移動のためのマウスボタンを設定します。 (上/下/左/右)
  * `scroll_mod = true` はスクロールベースのズームのための追加の修飾ボタンを設定します。 (true は中立)
  * `rotation_button = Mouse.left` はドラッグ回転のためのマウスボタンを設定します。 (パン、ティルト)

## その他の kwargs

いくつかのキーワード引数はフィールドを初期化するために使用されます。これには以下が含まれます。

  * `eyeposition = Vec3d(3)`: カメラの位置。
  * `lookat = Vec3d(0)`: カメラが焦点を合わせている点。
  * `upvector = Vec3d(0, 0, 1)`: 画面の上方向に対応する世界の方向。
  * `fov = 45.0` は視野です。カメラが正投影を使用する場合は無関係です。
  * `near = automatic` は近クリップ面の位置を設定します。カメラと近クリップ面の間にあるものは隠されます。0より大きくする必要があります。使用は `clipping_mode` に依存します。
  * `far = automatic` は遠クリップ面の位置を設定します。遠クリップ面よりも遠くにあるものは隠されます。使用は `clipping_mode` に依存します。`clipping_mode = :bbox_relative` の場合はデフォルトで `1`、`:view_relative` の場合は `2`、または `:static` の制限から導出された値になります。

アクティブなカメラでこれらのオブザーバブルを更新するには、適用されるために `update_cam(scene)` を呼び出す必要があります。`eyeposition`、`lookat` および/または `upvector` を更新するには、`update_cam!(scene, eyeposition, lookat, upvector = Vec3d(0,0,1))` が推奨されます。

カメラの位置と向きは、以下の関数を介して調整することもできます。

  * `translate_cam!(scene, v)` は、与えられたベクトル `v` によってカメラを移動します。
  * `rotate_cam!(scene, angles)` は、対応する角度でカメラをその軸の周りに回転させます。最初の角度はカメラの「右」、つまり画面の水平軸の周りを回転させ、2番目は上ベクトル/垂直軸の周り、または `fixed_axis = true` の場合は `Vec3d(0, 0, +-1)` の周りを回転させ、3番目はビュー方向、つまり画面の外側の軸の周りを回転させます。回転はカメラの現在の `rotation_center` を尊重します。
  * `zoom!(scene, zoom_step)` は、シーンを移動または回転させることなくズームレベルを変更します。`zoom_step` は `cam.zoom_mult` に乗算的に適用され、これは視野 (透視投影) または幅と高さ (正投影) の乗数として使用されます。
