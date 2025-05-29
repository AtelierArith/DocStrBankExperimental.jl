```
MadNLPSolver(nlp::AbstractNLPModel{T, VT}; options...) where {T, VT}
```

非線形プログラム `nlp::AbstractNLPModel` に関連付けられた新しい `MadNLPSolver` をインスタンス化します。オプションはオプションの引数として渡されます。

コンストラクタは、内部点アルゴリズムに必要なすべてのメモリを割り当てるため、メインアルゴリズムは割り当てなしで実行されます。
