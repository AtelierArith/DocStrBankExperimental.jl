```
checked(f, g, itr; kwargs...)
```

g(f, itr; kwargs...)を呼び出しますが、itr != nothingの場合のみです。

特定のエージェントのエッジにアクセスするすべてのVahana関数は、このエージェントに対する入ってくるエッジが存在しない場合、何も返さない可能性があるため、このケースを確認することがしばしば必要です。

例：

次のように書く代わりに

```@example
nids = neighborids(sim, id, Contact)
if nids != nothing
    foreach(nids) do nid
      add_edge!(sim, id, nid, Inform())
    end
end
```

checked関数を使用して次のように書くことができます。

```@example
checked(foreach, neighborids(sim, id, Contact)) do nid
    add_edge!(sim, id, nid, Inform())
end
```
