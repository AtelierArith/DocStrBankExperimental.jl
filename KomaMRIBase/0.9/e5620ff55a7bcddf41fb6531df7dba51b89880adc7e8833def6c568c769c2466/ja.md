```
motionlist = MotionList(motions...)
```

MotionList構造体。`NoMotion`の代わりに、`MotionList`構造体を用いて動的なファントムを定義することができます。これは1つ以上の[`Motion`](@ref)インスタンスで構成されています。

# 引数

  * `motions`: (`::Vector{Motion{T<:Real}}`) `Motion`インスタンスのベクター

# 戻り値

  * `motionlist`: (`::MotionList`) MotionList構造体

# 例

```julia-repl
julia>  motionlist = MotionList(
            Motion(
                action = Translate(0.01, 0.0, 0.02),
                time = TimeRange(0.0, 1.0),
                spins = AllSpins()
            ),
            Motion(
                action = Rotate(0.0, 0.0, 45.0),
                time = Periodic(1.0),
                spins = SpinRange(1:10)
            )
        )
```
