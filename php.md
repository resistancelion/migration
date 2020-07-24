# 4.x - 5.0
### functions
```
array_merge( array, mixed ) -> array_merge( array, array )
array_merge_recursive( array, mixed ) -> array_merge_recursive( array, array )
[ array_merge($array, 'new_element') -> array_merge( $array, array('new_element') ) ]

ip2long('whatever') -> FALSE || -1

An object with no properties is no longer considered "empty":
empty( $object ) -> false || true
```
### constants
```
Tokenizer:
PATH_TRANSLATED -> SCRIPT_FILENAME
T_ML_COMMENT -> T_COMMENT ;
```
### behaviour
```CLI:
$argc, $argv
-> always present || relies on variables_order setting ;

get_class(), get_parent_class(), get_class_methods(), __CLASS__, __METHOD__, and __FUNCTION__
-> returns NormalCase || before: lowercase

Extended / interfaced classes must be declared before use:
No forward use is supported

Declaration of identifiers after exit() and return keywords now working || ignored:
return; // _printb now can be called if the script was included
function _printb($what)
{
echo '<pre>' . $what . '</pre>';
}

including file twice produces fatal error: include -> include_once

include_once, require_once normalizes path on Windows platform (string case issue fix)

strrpos, stripos now finds substring instead of first character

$this variable cannot be assigne anymore

Array internal pointer (when passing not by-reference) inside the function won't recreate at every change approach:
optimisation, possible - value can be changed without copying array parameter

Function calls now has limited amount of arguments

Accessing an empty property now causes E_FATAL instead of E_WARNING

Creating class now returns reference instead of value, reason: objects now has reference logic

Comment blocks now disables HTML tags:
//t?> won't close php block

Clone() won't call parent's class __Construct method anymore

Object cannot be treated as array by default:
$SomeObject["property"] will produce error, if there's no ArrayAccess magic methods used

$HTTP_* variables is now relies on register_long_arrays setting
```
### Config
```
Added:
mail.force_extra_parameters - Force the addition of the specified parameters to be passed as extra parameters to the sendmail binary. These parameters will always replace the value of the 5th parameter to mail(), even in safe mode
register_long_arrays - allow/disallow PHP to register the deprecated long $HTTP_*_VARS
session.hash_function - select a hash function (MD5 or SHA-1)
session.hash_bits_per_character - define how many bits are stored in each character when converting the binary hash data to something readable (from 4 to 6)
zend.ze1_compatibility_mode - Enable compatibility mode with Zend Engine 1 (PHP 4) - enables old behaviour for objects
```
