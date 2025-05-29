```
imx
𝐢
```

`x` 軸まわりの回転に関連する四元数単位。Unicode 太字 `𝐢` としても入力できます（`\bfi<tab>` として入力可能）。

`im` が `Complex{Bool}` であるのと同様に、`imx` は `QuatVec{Bool}` であり、他の数値型（例えば `Float64`）のスカラーで乗算すると、その数値型の `QuatVec` に昇格し、スカラーを *加算* すると `Quaternion` に昇格します。

[`imy`](@ref) および [`imz`](@ref) も参照してください。

# 例

```jldoctest
julia> imx * imx
-1 + 0𝐢 + 0𝐣 + 0𝐤
julia> 1.2imx
 + 1.2𝐢 + 0.0𝐣 + 0.0𝐤
julia> 1.2 + 3.4imx
1.2 + 3.4𝐢 + 0.0𝐣 + 0.0𝐤
julia> 1.2 + 3.4𝐢
1.2 + 3.4𝐢 + 0.0𝐣 + 0.0𝐤
```
