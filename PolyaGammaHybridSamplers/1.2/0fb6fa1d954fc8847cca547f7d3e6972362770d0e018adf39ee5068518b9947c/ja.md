```
PolyaGammaHybridSampler(b::Real, z::Real, [method::PGSamplingMethod])
```

ポリヤ-ガンマ分布のサンプラーで、サドルポイント近似、デヴロイ法、正規近似、およびガンマの合計近似のハイブリッドを使用しています。これらの手法については、Windle et al. (2014)で説明されています。詳細はREADME.mdを参照してください。

# 引数

  * `b::Real`: ポリヤ-ガンマ分布の形状パラメータ。正でなければなりません。
  * `z::Real`: ポリヤ-ガンマ分布の指数傾斜パラメータ。
  * `method::PGSamplingMethod : ポリヤ-ガンマ分布からサンプリングするために使用されるメソッドを指定する列挙型オブジェクト。`DEVROYE`、`SADDLEPOINT`、`NORMALAPPROX`、`GAMMASUM`、または`DEVROYEPLUSGAMMASUM`のいずれかでなければなりません。省略した場合、`b`の値に基づいてメソッドが自動的に選択されます。

# 戻り値

  * `rand`または`rand!`を使用してサンプリングできる`PolyaGammaHybridSampler`オブジェクト。

# 例

```julia
julia> using PolyaGammaHybridSamplers
julia> s = PolyaGammaHybridSampler(1, 1.0)
julia> rand(s)
```

# 注意事項

  * 自動選択基準: 

      * `b > 170` -> `NORMALAPPROX`
      * `b >= 13` -> `SADDLEPOINT`
      * `b >= 1 && isinteger(b)` -> `DEVROYE`
      * `b > 1 && !isinteger(b)` -> `DEVROYEPLUSGAMMASUM`
      * `b >= 0` -> `GAMMASUM`
      * `b = 0` -> 0での退化分布

```
