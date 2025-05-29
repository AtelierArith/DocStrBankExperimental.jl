```
combiner(inds::Indices; kwargs...)
```

インデックス（タイプ Index）を単一の新しい Index に結合する combiner ITensor を作成します。そのサイズは与えられたインデックスの積です。例えば、インデックス `i1,i2,i3` が与えられた場合、combiner はこれらの3つのインデックスに加えて、`i1,i2,i3` の次元の積の次元を持つ追加のインデックスを持ちます。

内部的に、combiner ITensor は特別なストレージタイプを使用しており、実際のテンソル要素を保持するのではなく、インデックスを単一の Index に結合する方法に関する情報のみを保持します。通常の ITensor と combiner の積を取ると、インデックスを結合するための特別な高速アルゴリズムが使用されます。

与えられたインデックスから combiner が作成する新しい結合された Index を取得するには、`combinedind` 関数を使用します。

結合プロセスを元に戻す、つまり Index を元のものに戻すには、結合された Index を持つテンソルを combiner の共役または `dag` と収束させます。（もし combiner が ITensor `C` であれば、`dag(C)` で掛けます。）

### 例

```
# インデックス i と k を新しい Index ci に結合
T = random_itensor(i,j,k)
C = combiner(i,k)
CT = C * T
ci = combinedind(C)

# ci を i と k に戻す
TT = dag(C) * CT

# TT は T と同じになります
@show norm(TT - T) ≈ 0.0
```

```
          i  j  k
          |  |  |
 T   =    =======

          ci  i  k
          |   |  |
 C   =    ========

          ci  j
          |   |
 C * T =  =====
```
