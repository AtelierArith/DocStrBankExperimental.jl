Images.jlは、一般的な画像処理タスクに役立つ一連のパッケージをエクスポートする「アンブレラパッケージ」です。これらのパッケージのほとんどは、JuliaImages、JuliaArrays、JuliaIO、JuliaGraphics、およびJuliaMathにホストされています。

Imagesは、画像処理のためのアウトオブボックスツールキットを提供します。これは、`using Images`を実行すると、多くのパッケージが読み込まれ、それらが複数の小さなパッケージを必要とする可能性があることを意味します。例えば、`using ImageCore, ImageShow, ImageTransformations, FileIO`のようにです。しかし、パッケージを減らしたい場合は、特定のニーズに合わせた狭いツールボックスのために、これらの小さなパッケージを使用するのが良いでしょう。

JuliaImagesエコシステムのドキュメントは、https://juliaimages.org で見つけることができます。一部の依存関係には独自のドキュメントがあります。たとえば、Colors.jlのドキュメントは、Images.jlに含まれエクスポートされているにもかかわらず、https://juliagraphics.github.io/Colors.jl にホストされています。
