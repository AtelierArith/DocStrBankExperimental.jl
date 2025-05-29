readsas(filename::AbstractString;         encoding::AbstractString = "",         convert*dates::Bool = true,         include*columns::Vector = [],         exclude*columns::Vector = [],         string*array*fn::Dict = Dict(),         number*array*fn::Dict = Dict(),         column*types::Dict = Dict{Symbol,Type}(),         verbose_level::Int64 = 1)

SAS7BDATファイルを読み込みます。

`Encoding`は、ファイルに指定されたエンコーディングを使用して読み取れない場合にのみオーバーライドとして使用できます。 もし未知のエンコーディングに関する警告が表示された場合は、`iconv --list`コマンドを使用して、システムのサポートされているエンコーディングを確認してください。

`convert_dates == false`の場合、変換は行われず、日付列のための日数（または日時列のための秒数）が1960年1月1日からの経過日数として得られます。

デフォルトでは、すべての列が読み込まれます。 列のサブセットのみが必要な場合は、`include_columns`または`exclude_columns`のいずれかを指定できますが、両方を指定することはできません。 それらは、列のインデックスまたはシンボルの配列です。例：[1, 2, 3]または[:employeeid, :firstname, :lastname]

文字列列はデフォルトで`SASLib.ObjectPool`に格納されます。これは、重複値が多い場合によりスペース効率の良い配列のような構造です。 ただし、ユニークなアイテムが多すぎる場合（> 10%）は、自動的に通常の配列に切り替わります。

異なる種類の配列を使用したい場合は、`string_array_fn`辞書を介して配列コンストラクタを渡すことができます。 コンストラクタは、配列のサイズを表す単一の整数引数を取る必要があります。 通常のArray{String}型を使用したいだけの場合は、便利な`REGULAR_STR_ARRAY`関数を使用できます。

例として、`string_array_fn = Dict(:column1 => (n)->CategoricalArray{String}((n,)))`または`string_array_fn = Dict(:column1 => REGULAR_STR_ARRAY)`があります。

数値列については、`number_array_fn`パラメータを使用して独自の配列コンストラクタを指定できます。 たとえば、値を格納するための異なる種類の配列（例：SharedArray）があるかもしれません。

変換が必要な場合は、`column_type`引数を指定してください。 それは、列のシンボルをデータ型にマッピングする辞書である必要があります。

デバッグ目的で、`verbose_level`を1より大きい値に設定できます。 ボリュームレベル0はコンソールに何も出力せず、実質的に完全に静かなオプションです。
