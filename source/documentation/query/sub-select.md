---
title: ARQ - Sub Queries
---

ARQ includes support for nested SELECTs.  This was previously an ARQ extension but is now legal SPARQL 1.1

## Nested SELECT

A SELECT query can be placed inside a graph pattern to produce a
table that is used within the outer query. A nested SELECT
statement is enclosed in {} and is the only element in that group.

Example: find toys with more than five orders:

    PREFIX : <http://example/>
    SELECT ?x
    {
      ?x a :Toy .
      { SELECT ?x ( count(?order) as ?q ) { ?x :order ?order } GROUP BY ?x }
      FILTER ( ?q > 5 )
    }


[ARQ documentation index](index.html)
