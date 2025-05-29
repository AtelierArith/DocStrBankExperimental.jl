報酬を各ステップの後に得ることができるか、ゲームの終了時のみ得ることができるかを指定します。可能な値は [`STEP_REWARD`](@ref)（デフォルト）または [`TERMINAL_REWARD`](@ref) です。

!!! note
    [`TERMINAL_REWARD`](@ref) スタイルの環境は、[`STEP_REWARD`](@ref) スタイルの環境のサブセットとして見ることができます。MCTS のような一部のアルゴリズムでは、[`TERMINAL_REWARD`](@ref) スタイルの環境に対して、より効率的な実装があるかもしれません。

