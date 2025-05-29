new(clauses; max_var::Int = 0, configuration = nothing)::RawSolver

新しいソルバーを作成します。これは、寿命の終わりに自己破壊します。

オプションの引数は、予約されたリテラルの数 max_var と、Set([:default, :sat, :plain, :basic, :unsat]) の構成を指定できます。
