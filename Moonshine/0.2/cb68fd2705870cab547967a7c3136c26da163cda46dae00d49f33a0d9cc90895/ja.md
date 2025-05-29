```julia
struct Sequence
```

二重対立遺伝子マーカー（ハプロタイプ）の列。

[反復インターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration)と標準のビット演算を実装します。

!!! info
    ランダムコンストラクタは、[`Random.bitrand`](@extref)を介してマーカーの状態をサンプリングします。


# フィールド

  * `data::BitVector`

# コンストラクタ

```julia
Sequence(data)
Sequence(data)
```

[`packages/Moonshine/7JVTP/src/Sequence.jl:48`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sequence.jl)で定義されています。

```julia
Sequence()
```

[`packages/Moonshine/7JVTP/src/Sequence.jl:187`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sequence.jl)で定義されています。

```julia
Sequence(undef, n)
```

[`packages/Moonshine/7JVTP/src/Sequence.jl:189`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sequence.jl)で定義されています。

```julia
Sequence(rng, n)
```

[`packages/Moonshine/7JVTP/src/Sequence.jl:191`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sequence.jl)で定義されています。

```julia
Sequence(rng, minlength, maxlength)
```

[`packages/Moonshine/7JVTP/src/Sequence.jl:193`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Sequence.jl)で定義されています。

ここで：

  * `n`: マーカーの数
  * `rng`: 擬似乱数生成器
  * `minLength, maxLength`: 列の長さの範囲
