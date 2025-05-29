```
set_schemes(;
    # キーワード引数とそのデフォルト値
    time=SteadyState,
    divergence=Linear, 
    laplacian=Linear, 
    gradient=Orthogonal,
    limiter=nothing) = begin
    
    # スキームのためのNamedTuple定義を返します 
    (
        time=time,
        divergence=divergence,
        laplacian=laplacian,
        gradient=gradient,
        limiter=limiter
    )   
end
```

`set_schemes`関数は、ユーザーが解決するすべてのフィールドの離散化スキームを定義するのを助けるために、トップレベルAPIで使用されます。デフォルト値を提供するため、ユーザーは変更したいエントリを選択できます。

# 入力

  * `time`は時間スキームを設定するために使用されます（デフォルトは`SteadyState`）
  * `divergence`は発散スキームを設定するために使用されます（デフォルトは`Linear`）
  * `laplacian`はラプラススキームを設定するために使用されます（デフォルトは`Linear`）
  * `gradient`は勾配スキームを設定するために使用されます（デフォルトは`Orthogonal`）
  * `limiter`は勾配リミッターを使用するかどうかを指定するために使用されます。現在サポートされているリミッターには`FaceBased`と`MFaceBased`が含まれます（デフォルトは`nothing`）
