```
t8_element_first_descendant_face(ts, elem, face, first_desc, level)
```

Construct the first descendant of an element at a given level that touches a given face.

# Arguments

  * `ts`:[in] Implementation of a class scheme.
  * `elem`:[in] The input element.
  * `face`:[in] A face of *elem*.
  * `first_desc`:[in,out] An allocated element. This element's data will be filled with the data of the first descendant of *elem* that shares a face with *face*.
  * `level`:[in] The level, at which the first descendant is constructed

### Prototype

```c
void t8_element_first_descendant_face (const t8_eclass_scheme_c *ts, const t8_element_t *elem, int face, t8_element_t *first_desc, int level);
```
