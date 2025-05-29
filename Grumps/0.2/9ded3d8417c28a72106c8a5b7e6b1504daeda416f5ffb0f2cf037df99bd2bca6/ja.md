```
OptimOptionsδ( ; 
f_tol = 1.0e-8, 
g_tol = 1.0e-8, 
x_tol = 1.0e-6, 
iterations = 25, 
show_trace = false, 
store_trace = true, 
extended_trace = false )
```

内部最適化アルゴリズムのための*OptimOptions*最適化オプション変数を作成し、関数値の許容誤差、勾配の許容誤差、解の許容誤差、最大反復回数、トレースを表示するかどうか、トレースを保存するかどうか、拡張トレースを保持するかどうかを含みます。詳細については**Optim**パッケージを参照してください。

Grumpsの現在のバージョンは、トレース関連のパラメータをほとんど無視します。
