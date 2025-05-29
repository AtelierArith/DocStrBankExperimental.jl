```
strel_chain(A, B, ...)
strel_chain(As)
```

同じ次元の構造要素を連結して、より大きなものを構築します。

出力の次元は入力の次元と同じです。各SEの直積を取る[`strel_product`](@ref)も参照してください。

!!! note "構造要素の分解"
    膨張や侵食などのいくつかの形態学的操作`f`において、`se`がより小さなもの`se1, se2, ..., seN`に分解できる場合、`f(img, se)`は`f(...f(f(img, se1), se2), ..., seN)`と同等です。元の大きなものに対して`f`を適用するよりも、小さなSEに対して`f`を適用する方が効率的であるため、このトリックは画像の形態学で広く使用されています。


```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> img = rand(512, 512);

julia> se1, se2 = [centered(rand(Bool, 3, 3)) for _ in 1:2];

julia> se = strel_chain(se1, se2);

julia> out_se = dilate(img, se);

julia> out_pipe = dilate(dilate(img, se1), se2);

julia> out_se[2:end-1, 2:end-1] == out_pipe[2:end-1, 2:end-1] # 境界を除いて
true
```
