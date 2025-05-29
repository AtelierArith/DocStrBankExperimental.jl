`@multibreak` は、複数のネストされたループから一度に抜け出し、オプションで続行することを可能にします。

最も簡単な使い方は次の形式です。

```
using Multibreak

@multibreak for i = 1:5
    for j = 1:5
        break; break
    end
end
```

完全なドキュメントについては、/home/terasaki/.julia/packages/Multibreak/vatgU/test/tutorial.jl または https://github.com/GunnarFarneback/Multibreak.jl/blob/master/test/tutorial.jl のチュートリアルをお読みください。
