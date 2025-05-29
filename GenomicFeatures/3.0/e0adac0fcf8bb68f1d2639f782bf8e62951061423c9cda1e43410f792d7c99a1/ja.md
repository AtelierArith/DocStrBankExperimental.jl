```
coverage(intervals)
```

コレクションの区間のカバレッジを計算し、ランレングスエンコードされたカバレッジデータを含む `GenomicIntervalCollection` を返します。

例えば、次のような区間が与えられた場合：

```
[------]     [------------]
   [---------------]
```

この関数は、注釈付きのカバレッジを持つ新しい不連続区間のセットを返します：

```
[1][-2-][-1-][--2--][--1--]
```

# 例

```jldoctest
julia> intervals = [
           GenomicInterval("chr1", 1, 8),
           GenomicInterval("chr1", 4, 20),
           GenomicInterval("chr1", 14, 27)];

julia> coverage(intervals)
GenomicIntervalCollection{GenomicInterval{UInt32}} with 5 intervals:
  chr1:1-3  .  1
  chr1:4-8  .  2
  chr1:9-13  .  1
  chr1:14-20  .  2
  chr1:21-27  .  1
```
