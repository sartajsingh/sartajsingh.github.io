---
layout: page
title: "Self in Ruby"
description: "Meaning and use of self in Ruby"
tags: ['Ruby']
---

`Self` in Ruby has the same meaning as in our daily dictionary - the object of introspection i.e. Oneself. A more technical definition would be -
 `Self` gives you access to the current object in a program. 

The `self` keyword is a very interesting concept in Ruby. It is globally accessible and always returns the current object to you. At the topmost level, when `self` is used outside of any class or method , it will always return Main. Lets see what are the basic uses of `self` in Ruby. 



### When defined inside a class

Whenever `self` is used inside a class and outside any of its methods, it simply points to that particular class.

~~~ Ruby
class Ruby
  puts self
end
~~~

This use of `self` will return `Ruby` as expected i.e the class name.



### When defined inside a method
Whenever `self` is used inside a method, it will always point to the object that the method is called upon.

~~~ ruby
class Ruby
 def check
  puts self
 end 
end
~~~
~~~ ruby
obj = Ruby.new
puts obj
puts obj.text
~~~

Both the commands will return 

~~~ ruby 
#<Ruby:0x007fa8128525e8>
~~~
 i.e. the value of the instance obj.



### To define class methods (Singleton methods)

Singleton methods are those methods which can be called only by a single object which owns that method. For a method defined in a class ,the calling object will always be the class.

~~~ ruby
class GameOfThrones
 def self.amaze
   puts “GoT is amazing”
 end
end
~~~

The method `amaze` will be called only by using the class `GameOfThrones`. You can try it yourself.
simply calling amaze  will return :

~~~ ruby
NameError: undefined local variable or method 'amaze' for main:Object 
~~~

while calling the same method using the class name will give you the
desired output.

~~~ ruby
GameOfThrones.amaze
~~~

will return

~~~ ruby
GoT is amazing
~~~



### To define a singleton class
A more advanced way to make a bunch of methods use the class instance only is as follows

~~~ ruby
class GameOfThrones
  class<<self
    def daenerys
      puts “Daenerys is the mother of Dragons ”
    end
    def starks
      puts “Starks are attracted to death”
   end
 end
end
~~~

~~~ ruby 
GameOfThrones.starks
~~~
 will return

~~~ Ruby
Starks are attracted to death
~~~

and
 
~~~ ruby
starks
~~~
 will give an error . Similar concept is for the other method. Try it by yourself to know better.
