```
AutoVector(def=0.0,mini::Integer=1,maxi::Integer=0,miniloc::Integer=0)
AutoVector(f::Function,mini::Integer=1,maxi::Integer=0,miniloc::Integer=0)
AutoVector(v::Vector,mini::Integer=1,maxi::Integer=0,miniloc::Integer=0)
```

頻繁に次のように使用します

```
v = AutoVector(), defaulting to Float64, size 0
```

または     v = AutoVector(0), defaulting to Int64, size 0

AutoVectorは、その範囲の外に書き込まれると拡張されます。範囲の外を読み取ることは範囲を拡張せず、defを返します。

引数:

def–デフォルト要素、通常は0.0。AutoVector{T}の型Tを決定します。

miniとmaxiは、作成されたAutoVectorのインデックス範囲を指定します（論理インデックス、データベクトルのインデックスではありません）。

minilocは、データベクトル内のmini-1の位置で、デフォルトは0（データインデックス）です。

デフォルトから、関数から、またはベクトルを入れることによってAutoVectorを初期化できます。ほとんどの関数とコンストラクタは論理インデックスを扱い、データインデックスはデータベクトルdat内の位置を指し、通常は心配する必要はありません。
