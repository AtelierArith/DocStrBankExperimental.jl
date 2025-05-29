## `biconnected_components`

この関数は、対称行列を入力として必要とします。ユーザーの入力に応じて、この関数は各エッジに関連付けられた双連結成分番号、または関節点、またはその両方を返します。

## 入力

  * `A`: 隣接行列
  * オプションのキーワード入力

      * `art=true`: グラフの関節点を返します。
      * `components=true`: 各エッジに関連付けられた双連結成分ラベルを返します。

## 返り値

  * `Biconnected_components_output` 型を返し、以下を含みます。

`map` : 各エッジに関連付けられた双連結成分ラベル、 `articulation_points`: 頂点が関節点であるかどうかを示すブール配列、 `number`: グラフ内の双連結成分の数。

## 例

A = load*matrix*network("biconnected*example") B = MatrixNetwork(A) bcc = biconnected*components(B) map = bcc.map articulation*vector = bcc.articulation*points number*of*components = bcc.number
