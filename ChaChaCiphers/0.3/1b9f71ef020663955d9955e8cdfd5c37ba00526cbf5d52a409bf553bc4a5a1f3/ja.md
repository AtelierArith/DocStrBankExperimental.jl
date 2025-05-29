```
ChaChaStream <: AbstractChaChaStream
```

`ChaChaStream` は、ChaCha ストリーム暗号によって生成されたキーストリームへのアクセスを提供します。これは、Julia の乱数生成関数のための暗号的に安全な乱数生成器 (CRNG) として使用できます。

## 例

ランダムに生成されたキーとノンスを持つ `ChaChaStream` を作成します：

```jldoctest; setup = :(using ChaChaCiphers, Random)
julia> stream = ChaCha20Stream();
```

事前に指定されたキーとノンスを持つ `ChaChaStream` を作成し、それを使用してランダムデータを生成します：

```jldoctest; setup = :(using ChaChaCiphers, Random)
julia> key = UInt32.([
          0xe2e39848, 0x70bb974d, 0x845f88b4, 0xb30725e4,
          0x15c309dc, 0x72d545bb, 0x466e99e3, 0x6a759f91
       ]);

julia> nonce = UInt64(1234);

julia> stream = ChaCha20Stream(key, nonce);

julia> randn(stream)
0.7689072580509484

julia> randstring(stream, 'a':'z', 8)
"klmptewr"
```

関連情報: [`CUDAChaChaStream`](@ref)
