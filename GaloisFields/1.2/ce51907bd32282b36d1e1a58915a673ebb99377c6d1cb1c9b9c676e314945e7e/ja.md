# GaloisFields.jl - Juliaの有限体

|      **ビルドステータス**       |               **テストカバレッジ**                |
|:-----------------------:|:-----------------------------------------:|
| [![][c-i-img]][c-i-url] | [![カバレッジステータス][codecov-img]][codecov-url] |

## はじめに

このモジュールは、[有限体][galois-fields-wiki]を表す型を定義します。素数の順序と素数の冪の順序の両方の体をサポートしています。

[galois-fields-wiki]: https://en.wikipedia.org/wiki/Finite_field

## 概要

ガロア体を作成する最も簡単な方法は、`@GaloisField`および`@GaloisField!`マクロを使用することです。通常、前者は素数の順序の体に、後者は素数の冪の順序の体に使用します。素数の冪の場合、原始元の表示名/変数名を渡します。

```julia
using GaloisFields

const F = @GaloisField 29     # ℤ/29ℤ
const G = @GaloisField! 27 β   # ℤ/3ℤの次数3の拡張; βによって乗法的に生成される

F(2)^29 == F(2)
β^27 == β
```

感嘆符`!`は、マクロに副作用があることを伝えるために意図されています：たとえば、上記のコードでは、`β`という変数に値を割り当てます。

マクロは、体を指定するための特別な記号も受け入れます。これは入力が難しいですが（[docs][unicode-input]）、読みやすさが向上します：

```julia
const F = @GaloisField ℤ/29ℤ
const G = @GaloisField 𝔽₂₇ β
```

順序$q = p^n$の体の表現に独自の生成元を渡したい場合は、次のようにできます：

```julia
const F = @GaloisField! 𝔽₃ β^2 + β + 2
β^2 + β + 2 == 0
```

最後に、マクロが適切でない場合の関数インターフェースもあります：

```julia
const F = GaloisField(29)               # ℤ/29ℤ
const G, β = GaloisField(81, :β)        # ℤ/3ℤの次数4の拡張
const G, β = GaloisField(3, 4, :β)      # 同じ; 81を因数分解する必要がない
const F, β = GaloisField(3, :β => [2, 0, 0, 2, 1]) # 同じ; 独自の最小多項式を渡す
```

## 高速な乗算

場合によっては、[ゼッヒの対数][zech]を利用して高速な乗算を行います。デフォルトでは、体の順序が$2^{16}$未満で、特性が2でなく、原始元が乗法的生成元である場合にこれが行われます。ただし、次のいずれかを呼び出すことでこれをオーバーライドできます。

```julia
GaloisFields.enable_zech_multiplication(F)
GaloisFields.disable_zech_multiplication(F)
```

*乗算操作を行う前に*。原始元が*乗法的生成元でない*体に対してこの関数を呼び出すと、警告が表示されます。

[zech]: https://en.wikipedia.org/wiki/Zech's_logarithm

## 変換

独自の最小多項式を指定した場合、体間の変換については何の仮定も行いません。たとえば、次のように定義した場合：

```julia
const F = @GaloisField! 𝔽₂ β^2 + β + 1
const G = @GaloisField! 𝔽₂ γ^2 + γ + 1
```

次のような操作はエラーをスローします：

```julia
G(β)
```

数学的な理由は、体$F$と$G$が同型であるが、異なる同型が2つあるためです。("彼らは*標準的に*同型ではありません。") 同定を選択するには、`identify`関数を使用できます（これはデフォルトではエクスポートされていないため、完全なパスを使用します）：

```julia
GaloisFields.identify(β => γ^2)
GaloisFields.identify(γ => β^2)
```

これにより、次のような変換が可能になります：

```julia
G(β)
convert(F, γ + 1)
```

この区別の内部動作は、シンボル名に基づいています。したがって、$F$と$G$を*同じ*シンボルと最小多項式で定義すると：

```julia
const F = @GaloisField! 𝔽₂ β^2 + β + 1
const G = @GaloisField! 𝔽₂ β^2 + β + 1
```

それらは単に等しいと見なされ、変換は追加の作業なしに機能します。

## デフォルトの最小多項式の変換

最小多項式を指定しない場合、たとえば次のように使用する場合：

```julia
const F = @GaloisField! 𝔽₈₁ β
const G = @GaloisField! 𝔽₉ γ
```

その場合、[コンウェイ多項式][conway]を使用します。これらは互いに特別な互換性関係を持ち、変換を可能にします：

```julia
β^10 == γ
```

これは、`F`と`G`が同じ特性`p`を持つ場合に機能します。いずれかの順序が他方の冪である場合、より大きな体に変換します。そうでない場合、両方を順序$p^N$の体に変換します。ここで、$N$は$F$と$G$のℤ/pℤに対する拡張次数の最小公倍数です。

## フィールド拡張の塔の構築

有限体のいくつかの応用では、すでに定義された有限体の拡張を使用することが便利です。すなわち、$q^m$の型の拡張の$G$が、$q$の冪の$F$に対して、ここで$q = p^n$は整数$m, n$のいずれかです。すでに定義された有限体の拡張を構築することが可能です：

```julia
# 29要素の体を作成
F = @GaloisField 29
# 多項式x^2 - 2はF29上で不可約です
G = @GaloisField! F x^2 - 2
# 多項式y^3 + 2y - 2はG上で不可約です
H = @GaloisField! G   y^3 + 2y - 2
# GはHの部分体です
# Hは|G|^3要素を持ちます
```

## 謝辞

このパッケージは、[Frank Lübeck][lubeck]の[コンウェイ多項式のデータベース][db]を使用しています。セキュリティのために、このパッケージ用に[https経由でコピーを利用可能にしています][https-db]。これはインストールプロセスの一部としてダウンロードされます。

[conway]: https://en.wikipedia.org/wiki/Conway*polynomial*(finite_fields)

[c-i-img]: https://github.com/tkluck/GaloisFields.jl/workflows/CI/badge.svg [c-i-url]: https://github.com/tkluck/GaloisFields.jl/actions?query=workflow%3ACI

[codecov-img]: https://codecov.io/gh/tkluck/GaloisFields.jl/branch/master/graph/badge.svg [codecov-url]: https://codecov.io/gh/tkluck/GaloisFields.jl

[lubeck]: http://www.math.rwth-aachen.de/~Frank.Luebeck/index.html [db]: http://www.math.rwth-aachen.de/~Frank.Luebeck/data/ConwayPol/index.html?LANG=en [https-db]: https://gist.githubusercontent.com/tkluck/e1cd1746c69aa17e4a37114d22649627/raw/7fbe9763fae27f14924262ad03606f1c3af4400e/CPImport.txt [unicode-input]: https://docs.julialang.org/en/v1.1/manual/unicode-input/#Unicode-Input-1
