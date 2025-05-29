```
aws_event_loop_group_get_next_loop(el_group)
```

次のループを取得します。目的は、ループ間での負荷分散を可能にすることです。この負荷分散がどのように行われるかに依存すべきではありません。将来的に変更される可能性があります。現在は、各ループの負荷係数に基づいた「二者択一」アルゴリズムを使用しています。

### プロトタイプ

```c
struct aws_event_loop *aws_event_loop_group_get_next_loop(struct aws_event_loop_group *el_group);
```
