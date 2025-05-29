モジュール FiniteDifferences3D

3-D 有限差分計算のためのマクロを提供します。次元 x、y、z はそれぞれ 1 番目、2 番目、3 番目の配列次元を指します。このモジュールは数学に近い表記を可能にするために設計されており、その結果、提供されたマクロのネストされた呼び出し（例：`@inn_z(@inn_y(@d_xa(A)))`）は許可されていません（代わりに、単に `@d_xi(A)` と書くことができます）。追加のマクロは、呼び出し元のモジュールに簡単に追加して、欠けている機能をカバーできます。このモジュールは、モジュール ParallelStencil と共に使用することを意図しています。

# 使用法

```
using ParallelStencil.FiniteDifferences3D
```

# マクロ

###### 差分

  * [`@d_xa`](@ref)
  * [`@d_ya`](@ref)
  * [`@d_za`](@ref)
  * [`@d_xi`](@ref)
  * [`@d_yi`](@ref)
  * [`@d_zi`](@ref)
  * [`@d2_xi`](@ref)
  * [`@d2_yi`](@ref)
  * [`@d2_zi`](@ref)

###### 選択

  * [`@all`](@ref)
  * [`@inn`](@ref)
  * [`@inn_x`](@ref)
  * [`@inn_y`](@ref)
  * [`@inn_z`](@ref)
  * [`@inn_xy`](@ref)
  * [`@inn_xz`](@ref)
  * [`@inn_yz`](@ref)

###### 平均

  * [`@av`](@ref)
  * [`@av_xa`](@ref)
  * [`@av_ya`](@ref)
  * [`@av_za`](@ref)
  * [`@av_xi`](@ref)
  * [`@av_yi`](@ref)
  * [`@av_zi`](@ref)
  * [`@av_xya`](@ref)
  * [`@av_xza`](@ref)
  * [`@av_yza`](@ref)
  * [`@av_xyi`](@ref)
  * [`@av_xzi`](@ref)
  * [`@av_yzi`](@ref)

###### 調和平均

  * [`@harm`](@ref)
  * [`@harm_xa`](@ref)
  * [`@harm_ya`](@ref)
  * [`@harm_za`](@ref)
  * [`@harm_xi`](@ref)
  * [`@harm_yi`](@ref)
  * [`@harm_zi`](@ref)
  * [`@harm_xya`](@ref)
  * [`@harm_xza`](@ref)
  * [`@harm_yza`](@ref)
  * [`@harm_xyi`](@ref)
  * [`@harm_xzi`](@ref)
  * [`@harm_yzi`](@ref)

###### その他

  * [`@maxloc`](@ref)
  * [`@minloc`](@ref)

マクロタイプ `?<macroname>` の説明を見るには（`@` を含む）。
