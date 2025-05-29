```
# 一致による置き換え
populations!(data::PopData, rename::Dict)
populations!(data::PopData, rename::Vector{String})
populations!(data::PopData, samples::Vector{String}, populations::Vector{String})

```

`PopData`の人口名を変更または再割り当てするための複数のメソッド。

## 辞書を使用して名前を変更する

`PopData`の既存の人口IDを`population_name => replacement`の`Dict`を使用して変更します。

**例**

```
potatopops = Dict("1" => "Idaho", "2" => "Russet")
populations!(potatoes, potatopops)
```

## 文字列のベクターを使用して名前を変更する

新しい名前の数が現在のユニークな人口名の数と等しい場合、このメソッドは`unique()`を介して出現する順序で既存の人口を変更します。新しい人口名の数がサンプルの数と等しい場合、このメソッドは`sampleinfo(popdata)`に出現する順序で各サンプルに新しい人口名を割り当てます。

**例**

```
# 既存の人口を（2）名前変更
potatopops = ["Idaho", "Russet"]
populations!(potatoes, potatopops)

# すべての[44]サンプルに新しい名前を割り当てる
potatopops = repeat(["Idaho", "Russet"], inner = 22) ;
populations!(potatoes, potatopops)
```

## サンプルと新しい人口割り当てを使用して再割り当てする

各個体の人口を完全に再割り当てします。サンプル名のベクターと、それに対応する新しい人口名のベクターの2つを入力として受け取ります。これは、一部の個体の人口名を変更するのに便利です。

**例**

```
populations!(potatoes, ["potato_1", "potato_2"], ["north", "south"])
```
