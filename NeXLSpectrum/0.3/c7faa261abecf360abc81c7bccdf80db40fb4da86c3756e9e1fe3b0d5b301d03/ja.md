```
findsimilar(
    specs::AbstractArray{Spectrum{T}}; 
    atol = nothing, 
    rtol=1.5, 
    minspecs=3
)::Vector{Spectrum{T}}
findsimilar(
    specs::AbstractArray{Spectrum{T}},
    det::Detector,
    elm::Element; 
    atol = nothing, 
    rtol=1.5, 
    minspecs = 3
)::Vector{Spectrum{T}}
```

スペクトルのコレクションを平均に最も似ているものにフィルタリングし、残りのスペクトルが次のいずれかになるまで、最も似ていないスペクトルを順次削除します：

  * atol未満（atol != nothingの場合）
  * rtol * median(others)未満（rtol != nothingの場合）

これは、複製スペクトルのセットの中で、互いに十分に似ているものを見つけるのに役立ちます。
