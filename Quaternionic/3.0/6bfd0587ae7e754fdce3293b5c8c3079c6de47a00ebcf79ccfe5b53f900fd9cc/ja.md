```
imy
𝐣
```

`y` 軸まわりの回転に関連する四元数単位。Unicode 太字 `𝐣`（これは `\bfj<tab>` として入力できます）としても入力できます。

`im` が `Complex{Bool}` であるのと同様に、`imy` は `QuatVec{Bool}` であり、他の数値型（例えば `Float64`）のスカラーで乗算すると、その数値型の `QuatVec` に昇格し、スカラーを *加算* すると `Quaternion` に昇格します。

[`imx`](@ref) および [`imz`](@ref) も参照してください。

# 例

```jldoctest
julia> imy * imy
-1 + 0𝐢 + 0𝐣 + 0𝐤
julia> 1.2imy
 + 0.0𝐢 + 1.2𝐣 + 0.0𝐤
julia> 1.2 + 3.4imy
1.2 + 0.0𝐢 + 3.4𝐣 + 0.0𝐤
julia> 1.2 + 3.4𝐣
1.2 + 0.0𝐢 + 3.4𝐣 + 0.0𝐤
```
