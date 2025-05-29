```
colorbuffer(scene, format::ImageStorageFormat = JuliaNative; update=true, backend=current_backend(), screen_config...)
```

指定されたシーンまたは画面の内容を、色の行列にラスタライズして返します。返される型はバックエンドに依存しますが、RGBまたはRGBAのいずれかの形式になります。

  * `backend::Module`: Makieバックエンドであるモジュール。例えば、`backend = GLMakie`、`backend = CairoMakie`など。
  * `format = JuliaNative` : 標準のJulia画像の形式（次元が入れ替わり、1つが反転）でバッファを返します。
  * `format = GLNative` : GLMakie用のより効率的な形式のバッファを返し、変換なしでFFMPEGで直接使用できます。
  * `screen_config`: バックエンドに依存します。`?Backend.Screen`/`Base.doc(Backend.Screen)`で調べてください。
  * `update=true`: 制限をリセット/更新します。カメラの動きを保持したい場合はfalseに設定してください。
