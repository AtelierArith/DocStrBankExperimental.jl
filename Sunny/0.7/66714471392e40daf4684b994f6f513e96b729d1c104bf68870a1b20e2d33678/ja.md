結晶学的単位格子とその空間群対称性を記述するオブジェクト。コンストラクタは次のとおりです。

```
Crystal(filename; override_symmetry=false, symprec=nothing)
```

`filename`のパスにある`.cif`ファイルから結晶を読み込みます。`override_symmetry=true`の場合、空間群は原子の位置に基づいて推測され、返される単位格子はサイズが縮小される可能性があります。mCIFファイルの場合、返される値は磁気スーパーセルですが、`override_symmetry=true`の場合は除外されます。CIFファイルから空間群対称性の精度を推測できない場合は、`symprec`で指定する必要があります。返される`Crystal`の`latvecs`フィールドはオングストローム単位です。

```
Crystal(latvecs, positions; types=nothing, symprec=1e-5)
```

格子ベクトル`latvecs`の単位で、座標（0から1の間）を持つ原子位置`positions`の完全なリストから結晶を構築します。空間群対称性情報は自動的に[Spglibパッケージ](https://github.com/spglib/spglib)を使用して推測されます[1]。オプションのパラメータ`types`は、各原子に対して1つの文字列のリストであり、原子間の対称性の同等性を破るために使用できます。

```
Crystal(latvecs, positions, spacegroup; types=nothing, choice=nothing, symprec=1e-5)
```

`spacegroup`の対称性を使用して結晶を構築します。占有されたワイコフごとに1つの代表的な原子を指定する必要があります。`spacegroup`は1..230の数値または文字列（例：ヘルマン–マウゲンまたはホール記号）として指定できます。空間群番号のみが提供された場合、ITA標準設定[2]が適用され、[ビルバオ結晶学サーバー](https://www.cryst.ehu.es)の規約に一致します。複数のITA設定を許可する空間群記号が提供された場合、可能な曖昧さがエラーメッセージに含まれ、`choice`文字列が関与する可能性があります。

# 例

```julia
# .cifファイルから結晶を読み込む
Crystal("filename.cif")

# 両方の原子を指定して従来の立方体単位格子でBCC結晶を構築します。空間群229が推測されます。
latvecs = lattice_vectors(1, 1, 1, 90, 90, 90)
positions = [[0, 0, 0], [1/2, 1/2, 1/2]]
Crystal(latvecs, positions)

# CsCl結晶を構築します（2つの単純立方体サブ格子）。異なる原子タイプのため、空間群番号221が推測されます。
types = ["Na", "Cl"]
cryst = Crystal(latvecs, positions; types)

# 空間群番号227とワイコフ8aに属する単一の原子位置からダイヤモンド立方体結晶を構築します。
positions = [[1/8, 1/8, 1/8]]
cryst = Crystal(latvecs, positions, 227)

# 異なる原点の選択を使用して同等の結晶を構築します。
positions = [[0, 0, 0]]
cryst = Crystal(latvecs, positions, 227; choice="1")
```

[`lattice_vectors`](@ref)も参照してください。

## 参考文献

1. [A. Togo, K. Shinohara, I. Tanaka, *Spglib: a software library for crystal symmetry search* (2018) [arXiv:1808.01590]](https://arxiv.org/abs/1808.01590).
2. [International Tables of Crystallography, Volume A (2016)](https://doi.org/10.1107/97809553602060000114).
