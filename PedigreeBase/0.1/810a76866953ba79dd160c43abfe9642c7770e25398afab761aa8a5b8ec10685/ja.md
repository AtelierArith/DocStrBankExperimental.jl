```
pedlist,idtable = read_ped(filename [, integer, order, hasupg])
pedlist,idtable = read_ped(T, filename [, integer, order, hasupg])
```

系譜ファイルを読み込み、系譜リストを整数行列 `pedlist` (2 x *n*; ここで *n* は系譜に見つかった動物の数) に格納します。引数 `T` は `pedlist` のデータ型を定義し、デフォルトは Int です。この関数は、文字と整数の2種類のIDをサポートしています。

デフォルトでは、この関数は元のデータを文字として読み込み、整数に変換します。テーブルは辞書 `idtable` にあり、2番目の戻り値として返されます。IDが整数の場合、オプション `integer=true` を指定すると、関数は単に整数として読み込み、変換は行いません。テーブルは作成されないため、戻り値は `pedlist` のみになります。

整数コーディングでは、関数は動物フィールドに存在しないすべての父と母を実際の動物として扱い、それらの新しいエントリを作成します。これは、系譜ファイルが RENUMF90 によって「再番号付け」され、実際の動物のIDよりも大きいUPGコードを持つ未知の親グループ（UPG）である場合には適切ではありません。オプション `hasupg=true` は、父/母フィールドのUPGに対して何も行わないため、そのようなUPGコードは `pedlist` にそのまま残ります。系譜ファイルは、動物、父、母のIDの少なくとも3つのフィールドを持つ空白区切りのテキスト形式です。デフォルトでは、最初の3つのフィールドがこれらのIDに割り当てられます。

オプションの引数 `order` はフィールドの位置を変更します。デフォルトは `order=[1,2,3]` で、1番目のフィールドが動物、2番目が父、3番目が母に対応します。

### 例

```jldoctest
julia> using PedigreeTools;

# 文字データの場合
julia> pedlist,idtable = read_ped("pedigree.txt");

# Int32ストレージを使用した文字データの場合
julia> pedlist,idtable = read_ped(Int32,"pedigree.txt");

# 整数コーディングの場合
julia> pedlist = read_ped("pedigree.txt", integer=true);
```
