```
DampedNewtonDescent(; linsolve = nothing, initial_damping, damping_fn)
```

ダンピングを伴うニュートン降下アルゴリズムです。ダンピング係数は `damping_fn` 関数を使用して計算されます。降下方向は $(JᵀJ + λDᵀD) δu = -fu$ として計算されます。非正方形のヤコビ行列の場合、`Jδx = -fu` と `√λ⋅D δx = 0` を同時に解くことがデフォルトです。線形ソルバーが非正方行列を処理できない場合、通常の形の方程式 $(JᵀJ + λDᵀD) δu = Jᵀ fu$ を使用します。この因子分解はしばしばより速い選択ですが、最小二乗ソルバーほど数値的に安定していません。

返されるダンピング係数は非負の数でなければなりません。

### キーワード引数

  * `initial_damping`: 使用する初期ダンピング係数
  * `damping_fn`: ダンピング係数を計算するために使用する関数。この関数は [`NonlinearSolveBase.AbstractDampingFunction`](@ref) インターフェースを満たす必要があります。
