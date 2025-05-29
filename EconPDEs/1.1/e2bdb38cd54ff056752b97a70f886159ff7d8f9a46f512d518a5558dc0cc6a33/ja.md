```
pdesolve(f, grid, yend [, τs]; is_algebraic = OrderedDict(k => false for k in keys(yend)), bc = nothing)

は、任意の数の関数と最大状態変数を持つ偏微分方程式のシステムを解きます。Fを解く関数の数、Sを状態変数の数とします。

### 引数
*  f: は関数 (state, y) -> out です
where: 
   state は長さ S の実数のタプル（状態値のため）
   y は長さ F * 3 の実数のタプルで、関数とその状態での一次および二次導関数を含みます
   out は長さ F の名前付きタプルで、状態での関数の時間導関数の値を持ちます 
* grid は、各状態に対して AbstractVector（グリッドのため）を関連付ける OrderedDict です
* yend は、PDE のシステム内の各関数の終端値を与える OrderedDict です
* τs（オプション）は、PDE を解くための時間グリッドです。この場合、yend は時間 τs[end] での解に対応します
```
