```
SquirrelNoise5
```

SquirrelNoise5 32ビットランダムノイズ関数、元々はSquirrel Eiserlohによるものです。

元のC++コードについてはhttp://eiserloh.net/noise/SquirrelNoise5.hppを参照してください。

## フィールド

  * `seed::UInt32 = 0` ノイズ関数のシード。

## 例

```jldoctest
julia> noise(0,SquirrelNoise5())
0x16791e00

julia> noise(1,SquirrelNoise5())
0xc895cb1d

julia> noise(0,SquirrelNoise5(32))
0x9ef5c661
```
