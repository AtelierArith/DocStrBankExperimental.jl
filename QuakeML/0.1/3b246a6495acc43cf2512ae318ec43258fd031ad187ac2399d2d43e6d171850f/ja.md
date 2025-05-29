# QuakeML

地震イベントを説明するQuakeML形式のファイルを読み書きします。

## ユーザー関数

  * [`QuakeML.read`](@ref): QuakeMLファイルを読み込む
  * [`QuakeML.readstring`](@ref): 文字列からQuakeMLドキュメントを読み込む
  * [`preferred_focal_mechanism`](@ref): イベントのための優先焦点メカニズムを取得する
  * [`preferred_magnitude`](@ref): イベントのための優先マグニチュードを取得する
  * [`preferred_origin`](@ref): イベントのための優先起源を取得する
  * [`quakeml`](@ref): `print(io, quakeml(qml))`で書き込むことができるイベントのセットからXMLドキュメントを作成する
