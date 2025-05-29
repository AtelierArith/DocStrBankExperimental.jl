```
imz
𝐫
```

`z` 軸まわりの回転に関連する四元数単位。Unicode 太字 `𝐤` としても入力できます（これは `\bfk<tab>` として入力可能です）。

`im` が `Complex{Bool}` であるのと同様に、`imz` は `QuatVec{Bool}` であり、他の数値型（例えば `Float64`）のスカラーで乗算すると、その数値型の `QuatVec` に昇格し、スカラーを *加算* すると `Quaternion` に昇格します。

[`imx`](@ref) および [`imy`](@ref) も参照してください。

# 例

```jldoctest
julia> imz * imz
-1 + 0𝐢 + 0𝐣 + 0𝐤
julia> 1.2imz
 + 0.0𝐢 + 0.0𝐣 + 1.2𝐤
julia> 1.2 + 3.4imz
1.2 + 0.0𝐢 + 0.0𝐣 + 3.4𝐤
julia> 1.2 + 3.4𝐤
1.2 + 0.0𝐢 + 0.0𝐣 + 3.4𝐤
```
