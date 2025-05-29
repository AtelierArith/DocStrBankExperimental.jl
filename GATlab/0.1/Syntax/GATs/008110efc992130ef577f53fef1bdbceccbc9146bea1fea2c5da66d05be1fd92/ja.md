`AlgStruct`

AlgTypeConstructorのための糖衣構文であり、その型の要素を構築するAlgTermConstructorおよび射影項構築子を含みます。例えば、

```
struct Cospan(dom, codom) ⊣ [dom:Ob, codom::Ob]
  apex::Ob
  i1::dom->apex
  i2::codom->apex
end
```

は（バニラGATにおいて）次のように同等です：

```
Cospan(dom::Ob, codom::Ob)::TYPE 

cospan(apex, i1, i2)::Cospan(dom, codom) 
  ⊣ [(dom, codom, apex)::Ob, i1::dom->apex, i2::codom->apex]

apex(csp::Cospan(d::Ob, c::Ob))::Ob            
i1(csp::Cospan(d::Ob, c::Ob))::(d->apex(csp))
i2(csp::Cospan(d::Ob, c::Ob))::(c->apex(csp))

apex(cospan(a, i_1, i_2)) == a  
  ⊣ [(dom, codom, apex)::Ob, i_1::dom->apex, i_2::codom->apex]
i1(cospan(a, i_1, i_2)) == i_1 
  ⊣ [(dom, codom, apex)::Ob, i_1::dom->apex, i_2::codom->apex]
i2(cospan(a, i_1, i_2)) == i_2
  ⊣ [(dom, codom, apex)::Ob, i_1::dom->apex, i_2::codom->apex]

cospan(apex(csp), i1(csp), i2(csp)) == csp
  ⊣ [(dom, codom)::Ob, csp::Cospan(dom, codom)]
```
