モジュール FiniteDifferences2D

2次元有限差分計算のためのマクロを提供します。次元 x と y はそれぞれ1番目と2番目の配列次元を指します。このモジュールは数学的に近い表記を可能にするために設計されており、その結果、提供されたマクロのネストされた呼び出し（例：`@inn_y(@d_xa(A))`）は許可されていません（代わりに単に `@d_xi(A)` と書くことができます）。追加のマクロは、呼び出し元モジュールに簡単に追加して、欠けている機能をカバーすることができます。このモジュールは、モジュール ParallelStencil と共に使用することを意図しています。

# 使用法

```
using ParallelStencil.FiniteDifferences2D
```

# マクロ

###### 差分

  * [`@d_xa`](@ref)
  * [`@d_ya`](@ref)
  * [`@d_xi`](@ref)
  * [`@d_yi`](@ref)
  * [`@d2_xa`](@ref)
  * [`@d2_ya`](@ref)
  * [`@d2_xi`](@ref)
  * [`@d2_yi`](@ref)

###### 選択

  * [`@all`](@ref)
  * [`@inn`](@ref)
  * [`@inn_x`](@ref)
  * [`@inn_y`](@ref)

###### 平均

  * [`@av`](@ref)
  * [`@av_xa`](@ref)
  * [`@av_ya`](@ref)
  * [`@av_xi`](@ref)
  * [`@av_yi`](@ref)

###### 調和平均

  * [`@harm`](@ref)
  * [`@harm_xa`](@ref)
  * [`@harm_ya`](@ref)
  * [`@harm_xi`](@ref)
  * [`@harm_yi`](@ref)

###### その他

  * [`@maxloc`](@ref)
  * [`@minloc`](@ref)

マクロタイプ `?<macroname>` の説明を見るには（`@` を含む）。
