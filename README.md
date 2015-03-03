# Ordered Map for golang

OrderedMap is a Python port of OrderedDict implemented in golang.  

## Features
- Full support Key/Value for all data types
- Exposes an Iterator that iterates in order of insertion
- Full Get/Set/Delete map interface


## Download and Install 
  
`go get https://github.com/cevaris/ordered_map.git`


## Examples

### Create, Get, Set, Delete

```go
package main

import (
    "fmt"
    "github.com/cevaris/ordered_map"
)

func main() {

    // Init new OrderedMap
    om := ordered_map.NewOrderedMap()

    // Set key
    om.Set("a", 1)
    om.Set("b", 2)
    om.Set("c", 3)
    om.Set("d", 4)

    // Same interface as builtin map
    if val, ok := om.Get("b"); ok == true {
        // Found key "b"
        fmt.Println(val)
    }

    // Delete a key
    om.Delete("c")

    // Failed Get lookup becase we deleted "c"
    if _, ok := om.Get("c"); ok == false {
        // Did not find key "c"
        fmt.Println("c not found")
    }
    
    fmt.Println(om)
}
```


### Iterator

```go
n := 100
om := ordered_map.NewOrderedMap()

for i:= 0; i < n; i++ {
	// Insert data into OrdereMap
    om.Set(i, fmt.Sprintf("%d", i*ij))
}

// Iterate though values
// - Values iteration are in insert order
// - Returned in a key/value pair struct
for kv := range om.Iter() {
	fmt.Println(kv, kv.Key, kv.Value)
}
```

### Custom Structs

```go
om := ordered_map.NewOrderedMap()
om.Set("one", &MyStruct{1, 1.1})
om.Set("two", &MyStruct{2, 2.2})
om.Set("three", &MyStruct{3, 3.3})

fmt.Println(om)
// Ouput: OrderedMap[one:&{1 1.1},  two:&{2 2.2},  three:&{3 3.3}, ]
```
  
## For Development

Git clone project 

`git clone https://github.com/cevaris/ordered_map.git`  
  
Build and install project

`make`

Run tests 

`make test`







