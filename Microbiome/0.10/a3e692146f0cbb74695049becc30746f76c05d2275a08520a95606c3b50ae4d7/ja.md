```
insert!(cp::CommunityProfile, md; namecol=:sample)
```

`CommunityProfile`にメタデータ（`Tables.jl`テーブルの形式で）を追加します。1つの列（`namecol`）には`commp`に存在するサンプル名が含まれ、他の列には各サンプルのメタデータが含まれます。

開始する前に、すべての行のすべての値が`insert!`可能であることを確認し、そうでない場合はエラーをスローします。これにはメタデータテーブルを2回繰り返し処理する必要があり、遅くなる可能性があります。パフォーマンスが重要な場合は、代わりに`set!`を使用できますが、これにより既存のデータが上書きされます。
