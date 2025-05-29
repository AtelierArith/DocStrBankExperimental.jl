```
@rule Rulename(a::A_Type, b::B_Type, ...) begin ... end
```

Defines a rule named `Rulename`.  A singleton type named `Rulename` will be defined to represent the rule.  An [`install`](@ref) method is defined for that type which can be used to add the necessary nodes and connections to a Rete to implement the rule.

The default supertype of a rule struct is `Rule`.  When it is desirable to group rules together, one can define an abstract type that is a type descendant of [`Rule`](@ref) and use that as a dotted prefix to `RuleName`.  The `RuleName` in the @rule invocation is `MyGroup.MyRule` then the supertype of MyRule will be `MyGroup`, rather than [`Rule`](@ref).

A rule can have arbitrarily many parameters.  The parameter list can also include clauses with no variable name.  Such clauses identify the types of facts that the rule might assert.  Memory nodes for these types will be added to the Rete if not already present.  They will be added by the automatically generated `install` method.  See CUSTOM_INSTALL below.  There is no enforcement that all types that are emitted by the rule are listed here, but various introspective tools, as well as proper rule installation depend on this.

The body of the `@rule` expression implements the behavior of the rule.  It can perform any tests that are necessary to determine which, if any facts should be asserted.  This code is included in a function that has the same name as the rule itself.  This function is used as the `join_function` of the [`JoinNode`](@ref) that implements the rule.  The function declares a keyword argument named `emit` whose default value calls [`emit`](@ref). For testing and debugging purposes, the rule function can be invoked from the Julia REPL, perhaps passing `emit=println` to try the rule function independent of the rest of the network.

Within the body, `@reject`, `@rejectif` and `@continueif` can be used.

`@reject` will exit the rule body unconditionally and issue a debug log message.

The other two take a conditional expression.

`@rejectif` will exit the rule body and log a message if the condition succeeds.

`@continueif` will exit and log if the condition returns false.

The first expression of the rule can be a call-like expression of RULE_DECLARATIONS.  Its "parameters" can be declarations of one of the forms

``FORWARD*TRIGGERS(argument*names...)`

Only the inputs for the specified argument names will serve as forward triggers.  For backward compatibility, if there is no `RULE_DECLARATIONS` expression then all inputs are forward triggers.

Note that if a `RULE_DECLARATIONS` clause is included then any forwarde triggers must be explicitly declared.

``CUSTOM_INSTALL()`

No `install` method will be automatically generated.  The developer must implement an `install` method for this rule.
