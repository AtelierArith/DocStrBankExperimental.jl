```
getbyattrib(D::Vector{<:GMTdataset}[, index::Bool=false]; kw...)
```

または

```
filter(D::Vector{<:GMTdataset}; kw...)
```

または

```
findall(D::Vector{<:GMTdataset}; kw...)
```

GMTdatasetベクトルを取得し、`kw`キーワードで設定された条件に一致する要素のみを返します。これは、`D`の`attrib`フィールドに使用可能な情報が設定されていることを前提としています。

注意: $getbyattrib$の代わりに$filter$(..., `index=false`)または$findall$(..., `index=true`)を使用することができます。

### パラメータ

  * `attrib name(s)=value(s)`: 例で説明する方が簡単です: `NAME="Antioquia"`は、その属性/値の組み合わせを持つすべての要素を選択します。`NAME=("Antioquia", "Caldas")`は、これらの`NAME`属性を持つ要素を選択します。必要に応じて、いくつでも追加できます。2つの`kwargs`を使用する場合、2つ目は条件として機能します。$(..., NAME=("Antioquia", "Caldas"), feature_id=0)$は、属性`feature_id` = 0を持つ$Antioquia$と$Caldas$のすべての要素を選択することを意味します。
  * `invert, or reverse, or not`: `true`の場合、クエリ条件に一致しないすべてのセグメントを返します。
  * `attrib`または`att`: (古い構文) `att=(NAME_2="value",)`のように、attribname、attribvalueを持つNamedTupleです。複合一致を行いたい場合は、より多くの要素を使用します。例えば、`att=(NAME_1="val1", NAME_2="val2")`の場合、2つの条件に一致するセグメントのみが返されます。
  * `index`: この`位置`引数を`true`に設定すると、`att`条件に一致するセグメントのインデックスのみを返します。

### 戻り値

GMTdatasetのベクトル、またはクエリ条件に一致するセグメントのインデックスを持つIntのベクトルを返します。クエリが空のGMTdatasetを返す場合は`nothing`になります。

## 例:

```
D = filter(D, NAME_2="Porto");
```
