# haskell-99-problems

##### 1
```haskell
myLast::[a]->a
myLast (xs:[]) = xs
myLast (h:xs) = myLast xs
```

##### 2
```haskell
myButLast::[a]->a
myButLast (x:xs) 
	| length xs == 1 = x
	| otherwise = myButLast xs
```

##### 3
```haskell
elementAt::[a]->Integer->a
elementAt xs n = elementAt' xs 0 n

elementAt'::[a]->Integer->Integer->a
elementAt' (x:xs) c n  
	| c == n = x
	| otherwise = elementAt' xs (c+1) n
```

##### 4
```haskell
import Data.List (group)
-- Solution 4
myLength xs = sum $ map (\x->1) xs
```

##### 5
```haskell
myReverse [] = []
myReverse (x:xs) = myReverse xs ++ [x]

myReverse' xs = foldl (\x y -> y:x) [] xs
```

##### 6
```haskell
isPalindrome xs  
	|(myReverse xs) == xs = True
	| otherwise =False
```

##### 7
```haskell
data NestedList a = Elem a | List [NestedList a]
data E = Multiple Int Char | Single Char deriving (Show)

flatten (Elem a) = [a]
flatten (List a) = concatMap flatten a
```

##### 8
```haskell
compress xs = map(\(x:xs) -> x ) $ group xs
```

##### 9
```haskell
pack xs = group xs
```

##### 10
```haskell
encode xs = map (\all@(x:xs)-> (length all, x)) $ pack xs
```

##### 11
```haskell
encodeModified (n,e)
	| n > 1 = Multiple n e
	| otherwise = Single e
```
