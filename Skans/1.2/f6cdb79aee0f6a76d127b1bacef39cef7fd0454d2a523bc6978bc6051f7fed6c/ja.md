```
skan!(repo::Repo, pages::Vector{<:Page}; notify=true) -> Vector{PageScan}
```

`pages`を`repo`に保存された状態と比較します。変更された`pages`のベクターを返し、変更された各ページのためにリポジトリを更新します。変更されたページがない場合、ベクターは空です。
