```
function continuify(
	source::FEVectorBlock,
	operator = Identity;
	abs::Bool = false,
	broken = false,
	order = "auto",
	factor = 1,
	regions::Array{Int,1} = [0]) where {T,Tv,Ti,FEType,APT}
```

は、sourceの演算子評価をFEType H1PkのFE関数に補間します。すなわち、source有限要素型の任意の演算子評価のラグランジュ補間です。broken = trueは、区分的な補間を生成します。
