```
aws_profile_collection_release(collection)
```

プロファイルコレクションの参照カウントを減少させます。参照カウントがゼロになると、コレクションは破棄されます。NULLを返します。

### プロトタイプ

```c
struct aws_profile_collection *aws_profile_collection_release(struct aws_profile_collection *collection);
```
