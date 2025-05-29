```
   Phas = PhasEn(Sig)
```

データシーケンス（`Sig`）の位相エントロピー（`Phas`）推定値を返します。デフォルトのパラメータを使用します：角度分割数 = 4、時間遅延 = 1、対数 = 自然対数、

```
   Phas = PhasEn(Sig::AbstractArray{T,1} where T<:Real; K::Int=4, tau::Int=1, Logx::Real=exp(1), Norm::Bool=true, Plotx::Bool=false)
```

指定された「キーワード」引数を使用してデータシーケンス（`Sig`）の位相エントロピー（`Phas`）推定値を返します：

# 引数：

`K`     - 角度分割数（粗いグレイニング）、1より大きい整数  

```
           *注意：分割の開始は正のx軸に沿って行われます。この点はやや任意であるため、対称性のために偶数（できれば4の倍数）の分割を使用することをお勧めします。
```

`tau`   - 時間遅延、正の整数    

`Logx`  - 対数の底、正のスカラー 

`Norm`  - `Phas`値の正規化：    

```
         [false]  正規化なし
         [true]   分割数 Log(`K`) に対して正規化
```

`Plotx` - `Plotx` が true の場合、ポアンカレプロットを返します（デフォルト：false）  

# 参照： `SampEn`, `ApEn`, `GridEn`, `MSEn`, `SlopEn`, `CoSiEn`, `BubbEn`

# 参考文献：

```
   [1] Ashish Rohila and Ambalika Sharma,
       "Phase entropy: a new complexity measure for heart rate
       variability." 
       Physiological measurement
       40.10 (2019): 105006.
```
