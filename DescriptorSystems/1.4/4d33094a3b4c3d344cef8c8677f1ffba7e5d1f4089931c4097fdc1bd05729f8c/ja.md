```
timeresp(sys, u, t, x0 = 0; interpolation = "zoh", state_history = false, 
         fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (y, tout, x)
```

適切な記述子システム `sys = (A-λE,B,C,D)` の時間応答を、入力信号 `u` と `t` に基づいて計算します。時間ベクトル `t` は、定期的に間隔を空けた時間サンプルで構成されています。行列 `u` は `sys` の入力数と同じ数の列を持ち、その `i` 行目は時間 `t[i]` における入力値を指定します。離散時間モデルの場合、`u` は `sys.Ts > 0` の場合に `sys` と同じレートでサンプリングされる必要があり、`t` はすべての時間ステップが `sys.Ts` と等しいか、空のベクトルに設定できます。ベクトル `x0` は時間 `t[1]` における初期状態ベクトルを指定し、省略した場合はゼロに設定されます。

行列 `y` には `sys` の出力の結果としての時間履歴が含まれ、ベクトル `tout` には対応する時間サンプルの値が含まれます。`y` の `i` 行目には時間 `tout[i]` における出力値が含まれます。キーワードパラメータ `state_history = false` が使用される場合、行列 `x` には状態ベクトルの結果としての時間履歴が含まれ、その `i` 行目には時間 `tout[i]` における状態値が含まれます。デフォルトでは、状態履歴は計算されず、`x = nothing` です。

連続時間モデルの場合、入力値はサンプル間で補間されます。デフォルトでは、ゼロ次保持に基づく補間が使用されます。線形補間法は、キーワードパラメータ `interpolation = "foh"` を使用して選択できます。

デフォルトでは、制御不能な無限固有値と単純な無限固有値はペア `(A,E)` から排除されます。基礎となるペンシル操作アルゴリズムは、`fast = true`（デフォルト）の場合は列ピボットを用いたランクを明らかにするQR分解、または `fast = false` の場合はSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算努力は高くなります。

キーワード引数 `atol1`、`atol2` および `rtol` は、それぞれ `A`、`B`、`C`、`D` の非ゼロ要素に対する絶対許容誤差、`E` の非ゼロ要素に対する絶対許容誤差、および `A`、`B`、`C`、`D` および `E` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は正方行列 `A` と `E` の次数、`ϵ` は作業用マシンエプシロンです。キーワード引数 `atol` を使用して、同時に `atol1 = atol` および `atol2 = atol` を設定できます。
