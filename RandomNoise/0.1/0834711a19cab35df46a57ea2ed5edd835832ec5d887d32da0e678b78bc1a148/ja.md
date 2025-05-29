```
SquirrelNoise5x2 <: AbstractNoise{UInt64}
```

2つの `SquirrelNoise5()` を重ね合わせて作られた64ビットノイズ関数です。

## フィールド

  * `seed1::UInt32 = 0` 最初のシード
  * `seed2::UInt32 = 1` 2番目のシード

両方のシードが等しい場合にインスタンスを構築すると、`DomainError` が発生します。

## 例

```jldoctest
julia> sqnx2 = SquirrelNoise5x2()
SquirrelNoise5x2(0x00000000, 0x00000001)

julia> noise(0, sqnx2)
0xd40e6352d9ba8dce

julia> noise(1, sqnx2)
0x0f9b5434d68ee534
```
