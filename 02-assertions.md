---
layout: page
title: Testing
subtitle: Assertions
minutes: 10
---
> ## Learning Objectives {.objectives}
>
> *   Assertions are one line tests embedded in code.
> *   Assertions can halt execution if something unexpected happens.
> *   Assertions are the building blocks of tests.

Assertions are the simplest type of test. They are used as a tool for bounding
acceptable behavior during runtime. The assert keyword in python has the
following behavior:

~~~ {.python}
>>> assert True == False
~~~
~~~ {.output}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  AssertionError
~~~
~~~ {.python}
  >>> assert True == True
~~~
~~~ {.output}
  >>>
~~~

That is, assertions halt code execution instantly if the comparison is false.
It does nothing at all if the comparison is true. These are therefore a very
good tool for guarding the function against foolish (e.g. human) input:

~~~ {.python}
def mean(num_list):
    assert len(num_list) != 0
    return sum(num_list)/len(num_list)
~~~

The advantage of assertions is their ease of use. They are rarely more than one
line of code. The disadvantage is that assertions halt execution
indiscriminately and the helpfulness of the resulting error message is usually
quite limited.

Also, input checking may require decending into a rabbit hole of exceptional cases.
What happens when the input provided to the mean function is a string, rather
than a list of numbers?

> ## Insert an Assertion {.challenge}
>
> 1. Open a Jupyter Notebook
> 2. Create the following function:
>
> ~~~ {.python}
> def mean(num_list):
>   return sum(num_list)/len(num_list)
> ~~~
>
> 3. In the function, insert an assertion that checks whether the input is
> actually a list.
>
> Hint: Use the [isinstance function](https://docs.python.org/2/library/functions.html#isinstance).
>


Assertions are also helpful for catching abnormal behaviors, such as those that
arise with floating point arithmetic.

> ## Almost Equal {.challenge}
>
> Assertions are also helpful for catching abnormal behaviors, such as those
> that arise with floating point arithmetic. Using the assert keyword, how could
> you test whether some value is almost the same as another value?
>
> - My package, `mynum`, provides the number a.
> - Use the `assert` keyword to check whether the number a is greater than 2.
> - Use the `assert` keyword to check that a is equal to 2 within an error of 0.003.
>
> ~~~ {.python}
> from mynum import a
> # greater than 2 assertion here
> # 0.003 assertion here
> ~~~

## NumPy

The NumPy numerical computing library has a built-in function `assert_allclose`
for comparing numbers within a tolerance:

~~~ {.python}
from numpy.testing import assert_allclose
from mynum import a
assert_allclose(a, 2, atol=0.003, rtol=0)
~~~

These assertions give much more helpful error messages and have much more 
powerful features than the simple assert keyword. An even more powerful sibling 
of the assertion is the _exception_. We'll learn about those in the next 
lesson.

## More Practice

We'll use the Jelly Bean Code to look a little bit more at asserts and testing
code:
[https://github.com/rachelslaybaugh/JellyBeanCode](https://github.com/rachelslaybaugh/JellyBeanCode)

