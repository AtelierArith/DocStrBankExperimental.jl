```
SimplifiedLCMC([categories])
```

文字頻度データセット：簡体字テキストコーパスに基づく、標準的な中国語のランカスターコーパス。コーパスの詳細については、彼らの[ウェブサイト](https://www.lancaster.ac.uk/fass/projects/corpus/LCMC/default.htm)を参照してください。

文字頻度は、選択したカテゴリに基づいてのみ計算できます（有効なカテゴリキーと対応するカテゴリ名については`CJKFrequencies.LCMC_CATEGORIES`を参照してください）。無効なカテゴリは無視されます。

## 例

すべてのカテゴリを読み込む：

```julia-repl
julia> charfreq(SimplifiedLCMC())
DataStructures.Accumulator{String,Int64} with 45411 entries:
  "一路…   => 1
  "舍得"   => 9
  "５８"   => 1
  "神农…   => 1
  "十点"   => 8
  "随从"   => 9
  "荡心…   => 1
  "尺码"   => 1
  ⋮      => ⋮
```

または、サブセットのみを読み込む（引数は任意のイテラブルにできます）：

```julia-repl
julia> charfreq(SimplifiedLCMC("ABEGKLMNR"))
DataStructures.Accumulator{String,Int64} with 35488 entries:
  "废…  => 1
  "蜷"  => 1
  "哇"  => 13
  "丰…  => 1
  "弊…  => 3
  "议…  => 10
  "滴"  => 28
  "美…  => 1
  ⋮    => ⋮
```

## ライセンス/著作権

注意：このコーパスには、データを提供する人によって異なるライセンス情報が含まれています。

元のコーパスは主に非営利の研究のために提供されています。完全な[エンドユーザーライセンス契約](https://www.lancaster.ac.uk/fass/projects/corpus/LCMC/lcmc/lcmc_license.htm)を必ず確認してください。

[オックスフォードテキストアーカイブ](https://ota.bodleian.ox.ac.uk/repository/xmlui/handle/20.500.12024/2474)を通じて、このコーパスは[CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/)ライセンスの下で配布されています。
