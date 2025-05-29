```
xstar, fval, exitflag, info = DAQPBase.linprog(f,A,bupper)
xstar, fval, exitflag, info = DAQPBase.linprog(f,A,bupper,blower,sense)
```

は線形計画問題の解 `xstar` を見つけます

```
min_x	f' x
subject to 
    blower[1:ms]	<= x[1:ms] <= bupper[1:ms]
    blower[ms+1:m]  <= A*x 	   <= bupper[ms+1:m],
```

ここで `m = length(bupper)` および `ms = m-size(A,2)` です。

# 入力

  * `f`  			- 目的関数の線形項、nベクトル
  * `A`  			- 制約法線、`(m-ms) x n`-行列
  * `bupper` 		- 制約の上限、mベクトル
  * `blower` 		- 制約の下限、mベクトル（デフォルト: -Inf）
  * `sense` 		- 制約の種類、`m`-ベクトルのCints（デフォルト: 0）。例の種類:

      * `0` : 不等式
      * `5` : 等式

# 出力

  * `xstar` 		- ソルバーによって提供された解
  * `fval` 		- `xstar` の目的関数値。
  * `exitflag` 	- ソルバーからのフラグ (>0 成功, <0 失敗)
  * `info` 		- ソルバーからのプロファイリング情報を含むタプル。
