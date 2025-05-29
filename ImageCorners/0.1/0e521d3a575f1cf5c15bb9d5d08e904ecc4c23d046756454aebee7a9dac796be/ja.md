```
corners = imcorner_subpixel(img; [method])
         -> Vector{HomogeneousPoint{Float64,3}}
corners = imcorner_subpixel(img, threshold, percentile; [method])
         -> Vector{HomogeneousPoint{Float64,3}}
```

[`imcorner`](@ref) と同様ですが、コーナーをサブピクセル精度で推定します。サブピクセル精度は、最大応答値の4接続近傍を使用してコーナー応答値を補間することによって達成されます。補間スキームの詳細については、[`corner2subpixel`](@ref) を参照してください。
