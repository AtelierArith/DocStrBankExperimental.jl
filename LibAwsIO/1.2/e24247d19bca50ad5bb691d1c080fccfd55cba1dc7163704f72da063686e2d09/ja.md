```
aws_host_address_move(from, to)
```

`from`を`to`に移動します。この呼び出しの後、fromはもはや使用できません。ただし、別の移動またはコピー操作のために再利用することはできます。

### プロトタイプ

```c
void aws_host_address_move(struct aws_host_address *from, struct aws_host_address *to);
```
