```
estimate!(buffer::AbstractVector, b::SBit)
estimate!(buffer::AbstractVector, b::VecOrMat{SBit})
estimate(buffer::AbstractVector)
estimate(s::SBitstream)
```

`b`を`buffer`にプッシュし、現在の[`estimate`](#)を返します。
