```
estimate_background(data, box_size;
    location=SourceExtractorBackground(),
    rms=StdRMS(),
    itp=ZoomInterpolator(box_size),
    edge_method=:pad,
    [filter_size])
```

与えられた推定器をデータのウィンドウにマッピングして2D背景推定を行います。

この関数は、`box_size`のサイズのボックス内で背景を推定します。`size(data)`がボックスサイズの整数倍でない場合、2つのエッジメソッドがあります：`:pad`と`:crop`。デフォルトはパディングであり（画像データを失わないために推奨されます）、`box_size`が整数の場合、暗黙の形状は正方形になります（例：`box_size=4`は`box_size=(4,4)`と同等です）。

メッシュを評価するために、各ボックスは`location`に渡されて背景を推定し、その後`rms`に渡されて背景の平方根平均二乗値を推定します。これらは`median`や私たちの[背景推定器](@ref)のいずれかのように呼び出し可能なものであれば何でも構いません。

メッシュが作成されると、`filter_size`が指定されている場合は中央値フィルタリングが行われます。`filter_size`は整数またはタプルのいずれかであり、整数は`box_size`と同じ方法でタプルに変換されます。フィルタリングは`ImageFiltering.MapWindow.mapwindow`を介して行われます。`filter_size`は奇数でなければなりません。

フィルタリング（該当する場合）の後、メッシュは`itp`に渡され、入力と同じ解像度で背景の低次推定を再作成します。

!!! note
    `box_size`が入力サイズの整数倍でない場合、出力の背景とrms配列は同じサイズになりません。


# 関連情報

  * [位置推定器](@ref)、[RMS推定器](@ref)、[補間器](@ref)
