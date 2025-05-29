MutualInformationImageRegistrationは、相互情報量を使用して画像登録を行います。

このパッケージの使用方法についての完全な例を示します：

```jldoctest
using MutualInformationImageRegistration, MutualInformationImageRegistration.FastHistograms, Random

# 登録のための中間変数を保持するために使用されるコンテナを作成します
mi = MutualInformationContainer(
    create_fast_histogram(
        FastHistograms.FixedWidth(),
        FastHistograms.Arithmetic(),
        FastHistograms.NoParallelization(),
        [(0x00, 0xff, 4), (0x00, 0xff, 4)],
    ),
)

# 登録する小さな画像が引き出される完全な画像を作成します
full_image = rand(UInt8, 500, 300)
view(full_image, 300:330, 200:220) .= 0xff

# 固定画像は、他の画像が登録される画像です
fixed = full_image[(300-10):(330+10), (200-10):(220+10)]

# 最大シフトは最大検索範囲です
MAX_SHIFT = 11
# パディングは、より高品質な登録のためにbboxを拡張するために使用されます
padding = [-10, -10, 10, 10]

# 中間データを保持するためのバッファが必要です
buffer = Array{UInt8}(undef, (size(fixed) .+ (MAX_SHIFT * 2))...)

# 移動するbboxにランダムなシフトを導入します
expected_x = rand(-5:5)
expected_y = rand(-5:5)

# 固定画像に対してbbox（移動するbboxと呼ばれる）で与えられた画像を登録します
shift, mm, mms = register!(
    mi,
    full_image,
    fixed,
    [300, 200, 330, 220] .+ padding .+ [expected_x, expected_y, expected_x, expected_y],
    MAX_SHIFT,
    MAX_SHIFT,
    buffer,
)

# 得られるシフトは、適用したシフトの等しい反対であるべきです
shift == (-expected_x, -expected_y)

# 出力

true
```

`MutualInformationContainer`を構築する際に使用できる非エクスポートの特性`NoParallelization`と`SIMD`も確認してください。`NoParallelization`がデフォルトであり、他の特性を使用して相互情報量計算の実行方法をカスタマイズできます。
