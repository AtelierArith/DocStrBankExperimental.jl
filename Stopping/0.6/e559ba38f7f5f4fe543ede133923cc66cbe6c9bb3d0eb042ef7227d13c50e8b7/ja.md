タイプ: 状態のリスト

コンストラクタ:

`ListofStates(:: AbstractState)`

`ListofStates(n :: Int, :: Val{AbstractState})`

`ListofStates(n :: Int, list :: Array{AbstractState,1})`

`ListofStates(state :: S; n :: Int = -1, kwargs...)`

注意:

  * `n != -1` の場合、最大で n の `AbstractState` を格納します。
  * `ListofStates` は、属性リストが最初のコンポーネントが `AbstractState` で、2番目のコンポーネントが `ListofStates` (または `VoidListofStates`) であるペアの配列であるため、状態のサブリストを再帰的に処理します。

例: `ListofStates(state)`     `ListofStates(state, n = 2)`     `ListofStates(-1, Val{NLPAtX}())`     `ListofStates(-1, [(state1, VoidListofStates), (state2, VoidListofStates)], 2)`    
