```
pdepe(m, pdefunction, icfunction, bdfunction, xmesh ; params=SkeelBerzins.Params(tstep=Inf), kwargs...)
```

1Dの楕円型PDEを、[1]で説明されている空間離散化法を使用して解きます - [`pdepe`](@ref)の変種を使用して定常問題を解きます。暗黙のオイラー法の1ステップを実行します。

入力引数:

  * `m`: 問題の対称性を指すスカラー。`m=0`、`m=1`、または`m=2`のいずれかの値を取ることができ、それぞれ直交座標、円筒座標、または球座標を表します。
  * `pdefunction`: 関数。容量、フラックス、およびソース項を使用してPDEの定式化を定義します（容量項は0に設定する必要があります）。
  * `icfunction`: 関数。ニュートンソルバーに使用される初期値を定義します。
  * `bdfunction`: 関数。問題の境界条件を定義します。
  * `xmesh`: ユーザーが解を得ることを意図している空間メッシュを表す1D配列。

キーワード引数:

  * `params`: ソルバーからのキーワード引数を含む[`SkeelBerzins.Params`](@ref)構造体を定義します。
  * `kwargs`: [`SkeelBerzins.Params`](@ref)構造体を使用する代わりに、ユーザーはこの特定の構造体から直接フィールドをソルバーに渡すことができます。

空間離散化`xmesh`で定義された点で利用可能な解を持つ1D配列を返します。
