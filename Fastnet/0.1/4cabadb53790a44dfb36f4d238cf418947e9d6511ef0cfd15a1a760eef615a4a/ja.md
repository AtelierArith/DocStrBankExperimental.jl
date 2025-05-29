```
FastNet(n,k,c,tlist;<keyword arguments>)
```

ネットワーク構造を表すFastNetオブジェクトを作成します。

最大*n*ノード、最大*k*リンクのメモリが割り当てられます。ノードは*c*の異なる状態のいずれかにあることができます。

引数tlistはLinkTypeの配列またはタプルです。このリストは、ネットワークにとって重要なリンクのタイプを示します。たとえば、疫学シミュレーションでは、感染したノードと感受性のあるノードの間のリンクに特に関心があります。FastNetは、tlistにリストされている状態のリンクの非常に迅速なカウント、選択などを可能にするために必要な帳簿管理を行います。

tlistの要素の順序は任意ではないことに注意してください。FastNetは、tlistの最初の要素に一致するリンクをリンク状態1にあると考えます。リンク状態2には2番目のタイプに一致するリンクが、そしてそのように続きます。

警告: ネットワーク内の各リンクは、同時に1つの状態にしか存在できません。重複するリンクタイプを含むtlistを渡すこと（例: [LinkType([1,2],3),LinkType(3,1)] ）は、ArgumentErrorを引き起こします。

FastNetは、いくつかのオプションのキーワード引数をサポートしています：

  * nodealias : 出力でノード状態の名前として使用される文字列のベクトル
  * linkalias : 出力でリンク状態の名前として使用される文字列のベクトル
  * rng : カスタム乱数生成器を指定します

ネットワークは最初は空です（すなわち、ヌルグラフ）。

# 例

```jldoctest
julia> using Fastnet

julia> FastNet(10,9,1,[])
ノード0およびリンク0のネットワーク

julia> FastNet(100,1000,3,[LinkType(1,2),LinkType(3,"*",1)])
ノード0およびリンク0のネットワーク

julia> using Random

julia> mt = MersenneTwister(1234);

julia> const S=1;

julia> const I=2;

julia> SI_link=LinkType(S,I)
リンクの形式:  (1) --- (2)

julia> net=FastNet(10000,60000,2,[SI_link],nodealias=["S","I"],linkalias=["S-I"],rng=mt)
ノード0およびリンク0のネットワーク
```
