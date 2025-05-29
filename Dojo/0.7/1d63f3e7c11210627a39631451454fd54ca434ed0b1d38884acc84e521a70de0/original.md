```
JointConstraint{T} <: Constraint{T}

constraint restricting translational and rotational degrees of freedom between two Body objects.

id: a unique identifying number
name: a unique identifying name
translational: Translational
rotational: Rotational
spring: flag for joint springs on
damper: flag for joint dampers on
parent_id: identifying number for parent Body{T}
child_id: identifying number for child Body{T}
minimal_index: indices for minimal coordinates
impulses: joint impulses that maintain constraint between two Body{T} objects
```
