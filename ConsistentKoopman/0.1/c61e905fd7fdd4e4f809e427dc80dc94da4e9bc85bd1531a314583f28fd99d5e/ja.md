```
diffProjection(u::Matrix{Float64}, σ::Matrix{Float64}, v::Matrix{Float64};
s::Integer, L::Integer, m::Integer, q::Integer)

未テスト 

拡散の固有関数を物理空間に投影し、SVDからの線形演算子成分を使用します
（すなわち、diffSVDの結果）、10.1073/pnas.1118984109の付録から

引数
=================
- u, σ, v: diffSVD()から、すなわち [u, σ, v] = diffSVD()

キーワード引数
=================
- s: 時間モードが計算されるサンプル数
- L: 計算された拡散固有関数の数
- m: 物理空間の次元
- q: 遅延の数（遅延がない場合は q = 1）
```
