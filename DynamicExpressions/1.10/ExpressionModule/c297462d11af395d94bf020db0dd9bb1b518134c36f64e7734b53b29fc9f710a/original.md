```
Expression{T, N, D} <: AbstractExpression{T, N}
```

(Experimental) Defines a high-level, user-facing, expression type that encapsulates an expression tree (like `Node`) along with associated metadata for evaluation and rendering.

# Fields

  * `tree::N`: The root node of the raw expression tree.
  * `metadata::Metadata{D}`: A named tuple of settings for the expression,   such as the operators and variable names.

# Constructors

  * `Expression(tree::AbstractExpressionNode, metadata::NamedTuple)`: Construct from the fields
  * `@parse_expression(expr, operators=operators, variable_names=variable_names, node_type=Node)`: Parse a Julia expression with a given context and create an Expression object.

# Usage

This type is intended for end-users to interact with and manipulate expressions at a high level, abstracting away the complexities of the underlying expression tree operations.
