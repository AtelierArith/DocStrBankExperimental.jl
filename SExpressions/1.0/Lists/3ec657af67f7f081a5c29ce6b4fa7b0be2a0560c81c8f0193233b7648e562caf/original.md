An immutable singly linked list, which may be improper.

A list is either `Nil` (empty) or `Cons`, where the first element is an arbitrary object and the second element is a list. The `List` type, however, includes all instances of `Cons`, including those for which the second element is not a list. Such `List` instances are called improper lists, which are allowed because they are used in many lisp dialects.
