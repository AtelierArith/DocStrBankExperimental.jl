```
@scalarsurfacemetric(name)
```

時間変化するスカラー表面メトリックを返す関数は、`name(state,constraint,sys::ILMSystem,t,bodyid,[,kwargs...])`というシグネチャを持つべきです。ここで、`state`は`state(zeros_sol(sys))`によって返されるのと同じ型の解ベクトルであり、`constraint`は`constraint(zeros_sol(sys))`によって返されるのと同じ型であり、`sys`はシステム構造体、`t`は時間、`bodyid`はボディID、`kwargs`は追加のキーワード引数です。このマクロは、その関数を拡張して、例えば`name(integrator,bodyid)`のように積分器でも動作するようにし、また解の履歴配列`sol`に対しても、例えば`name(sol::ODESolution,sys,t,bodyid)`のように動作します。これは、解の配列に明示的に存在しない`t`の値に対して補間を使用します。また、`t`の値の範囲を取ることもでき、例えば`name(sol::ODESolution,sys,0.1:0.01:0.2,bodyid)`のように使用できます。最後に、`name(sol::ODESolution,sys,bodyid)`を単に取ることで、全履歴を返すこともできます。
