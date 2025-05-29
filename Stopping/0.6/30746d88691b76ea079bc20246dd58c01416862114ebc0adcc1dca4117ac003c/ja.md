`add_to_list!`: 最大サイズ n のリストに State を追加します。n+1 番目の State が追加されると、リストの最初のものが削除されます。与えられた State は、リストに追加される前に圧縮されます（State.copy*compress*state を介して）。

`add_to_list!(:: AbstractListofStates, :: AbstractState; kwargs...)`

注意:

  * kwargs は compress_state 呼び出しに渡されます。
  * `VoidListofStates` に対しては何もしません。

関連情報: ListofStates, State.compress*state, State.copy*compress_state
