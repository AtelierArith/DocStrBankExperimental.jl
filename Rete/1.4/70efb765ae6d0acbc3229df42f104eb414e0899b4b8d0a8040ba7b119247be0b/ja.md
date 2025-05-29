JoinNodeは、複数の入力ストリーム間での結合操作を実装します。 `join_function`の最初の引数はJoinNode自体です。残りの引数は、結合ノードの入力ストリームから来ます。 `join_function`は、主張したい新しい事実ごとに`emit`を呼び出す必要があります。
