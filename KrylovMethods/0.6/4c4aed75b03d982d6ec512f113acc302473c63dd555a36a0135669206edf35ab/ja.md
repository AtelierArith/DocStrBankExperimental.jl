blockCG(A,B,X)

前処理共役勾配法による解法

A * X = B

入力:

```
A           - 行列または A*x を計算する関数
B           - 右辺の配列
tol         - 誤差許容値
maxIter     - 最大反復回数
M           - 前処理器、M\x を計算する関数
X           - 初期推定値の配列（上書きされる）
out         - 出力フラグ（-1: 出力なし、0: エラーのみ、1: 最終状態、2: 各反復の残差ノルム）
ortho       - 再直交化のフラグ（デフォルト: false）
pinvTol     - 擬似逆行列の許容値（デフォルト: eps(T)*size(B,1)）
storeInterm - 反復結果を保存するフラグ（デフォルト: false）
```

出力:

X       - 近似解（!storeInterm の場合は 2D 配列、そうでない場合は 3D 配列）   flag    - 終了フラグ（0 : 望ましい許容値達成、   					 -1 : 収束せずに maxIter に達した   					 -9 : 右辺がゼロだった）   err     - 相対残差のノルム、すなわち norm(A*X-B)/norm(B)   iter    - 反復回数   resvec  - 各反復の相対残差のノルム

参考文献:

```
O'Leary, D. P. (1980). The block conjugate gradient algorithm and related methods.
Linear Algebra and Its Applications, 29, 293–322. http://doi.org/10.1016/0024-3795(80)90247-5
```
