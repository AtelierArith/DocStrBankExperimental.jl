```
aws_profile_collection_acquire(collection)
```

プロファイルコレクションの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じプロファイルコレクションを返します。

### プロトタイプ

```c
struct aws_profile_collection *aws_profile_collection_acquire(struct aws_profile_collection *collection);
```
