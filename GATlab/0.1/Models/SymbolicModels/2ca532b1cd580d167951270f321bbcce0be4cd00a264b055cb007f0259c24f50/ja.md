GATの構文における式のベースタイプ。これは、Catlabとの後方互換性のために使用される`AlgTerm`の代替です。

私たちは、2-カテゴリーの理論におけるオブジェクト、モルフィズム、2-モルフィズムなど、理論内の各*型コンストラクタ*に対してJuliaタイプを定義します。もちろん、Juliaの型システムは依存型をサポートしていないため、型パラメータはJuliaタイプに組み込まれています。（それらは式インスタンスの追加データとして保存されます。）

具体的なタイプは、Juliaのコアタイプ`Expr`に構造的に似ています。しかし、*項コンストラクタ*は`head`フィールドとしてではなく、型パラメータとして表現されます。これにより、Juliaの型システムを使用したディスパッチがより便利になります。
