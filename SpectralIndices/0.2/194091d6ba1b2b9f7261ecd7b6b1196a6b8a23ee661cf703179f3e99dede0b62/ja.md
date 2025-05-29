```
get_indices(online::Bool = false)
```

スペクトルインデックスのJSONデータを取得します。

# 引数

  * `online::Bool = false`: GitHubリポジトリから最新のインデックスリストを直接取得するか（オンライン）、ローカルコピーから取得するか（オフライン）を指定します。

# 戻り値

  * `dict`: スペクトルインデックスデータを含む辞書。

# 例

```julia
# ローカルコピーからスペクトルインデックスを取得する（オフライン）
indices = get_indices()

# オンラインリポジトリから最新のスペクトルインデックスを取得する
indices = get_indices(true)
```
