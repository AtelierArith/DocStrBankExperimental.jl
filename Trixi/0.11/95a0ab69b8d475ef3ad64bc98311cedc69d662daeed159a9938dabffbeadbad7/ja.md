```
semidiscretize(semi::SemidiscretizationHyperbolicParabolic, tspan,
               restart_file::AbstractString)
```

セミ離散化 `semi` を時間区間 `tspan` の分割ODE問題としてラップし、[SciMLエコシステム](https://diffeq.sciml.ai/latest/) の `solve` に渡すことができます。放物線的な右辺は分割ODE問題の最初の関数であり、SciMLエコシステムのIMEX法の暗黙的部分によってデフォルトで使用されます。

初期条件などは `restart_file` から取得されます。
