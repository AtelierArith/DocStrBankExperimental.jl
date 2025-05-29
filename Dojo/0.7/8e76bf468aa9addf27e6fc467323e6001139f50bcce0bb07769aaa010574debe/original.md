```
ContactConstraint{T} <: Constraint{T}

constraint containing information for contact node.

id: unique identifying number 
name: unique identifying name 
model: type of contact model: ImpactContact, LinearContact, NonlinearContact 
parent_id: identifying number of Body experiencing contact 
child_id: always 0
impulses: contact impulses applied to Body 
impulses_dual: dual contact impulses, used by solver to enforce correct contact behaviors
```
