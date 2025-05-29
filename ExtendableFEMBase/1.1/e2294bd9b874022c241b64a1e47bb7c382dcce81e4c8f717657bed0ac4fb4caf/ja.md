```
struct FESpace{Tv, Ti, FEType<:AbstractFiniteElement,AT<:AssemblyType}
	name::String                          # 有限要素空間のフルネーム（メッセージで使用）
	broken::Bool                          # trueの場合、壊れたdofマップが生成される
	ndofs::Int                            # dofの総数
	coffset::Int                          # コンポーネントdofのオフセット
	xgrid::ExtendableGrid{Tv,Ti}          # xgridへのリンク
	dofgrid::ExtendableGrid{Tv,Ti}	      # dof番号付けに使用される（サブ）グリッドへのリンク（xgridと等しいか、xgridの子グリッドであることが期待される）
	dofmaps::Dict{Type{<:AbstractGridComponent},Any} # dofマップを持つバックパック
    interpolators::Dict{Type{<:AssemblyType}, Any} # 補間子を持つバックパック
end
```

パラメータとして有限要素タイプを持ち、dofマップ（CellDofs、FaceDofs、BFaceDofs）と追加のグリッド情報を保持し、必要に応じて係数を保持する配列へのアクセスを提供する構造体です。
