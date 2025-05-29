状態をキャッシュして、`state(env)`が`env`との次のインタラクションの前に常に同じ結果を返すようにします。この関数は、いくつかの環境が各`state(env)`の間に状態を持つため便利です。例えば: `StateTransformedEnv(StackFrames(...))`。
