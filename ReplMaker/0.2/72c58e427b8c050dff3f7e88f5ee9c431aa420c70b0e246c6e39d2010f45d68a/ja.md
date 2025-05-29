`REPL.LineEdit.transition`の便利な使用を実現する拡張。

いつ

  * 3つの引数（action, mistate, mode）を与えると、`REPL.LineEdit.transition`と等しくなります。
  * 2つの引数（mistate, mode）を与えると、デフォルトの'action'が現在のバッファをターゲットREPLモードにコピーします。
  * 1つの引数（mode）を与えると、actionは2つの引数の場合と同じで、'mistate'はデフォルトで`Base.active_repl.mistate`になります。
