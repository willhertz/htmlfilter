
 PHPMailer/Extras htmlfilter.inc
 ---------------
 This set of functions allows you to filter html in order to remove
 any malicious tags from it. Useful in cases when you need to filter
 user input for any cross-site-scripting attempts.
 
 Copyright (C) 2002-2004 by Duke University

 @Author  Konstantin Riabitsev <icon@linux.duke.edu>
 @Author  Jim Jagielski <jim@jaguNET.com / jimjag@gmail.com>
 @Version 1.1 ($Date$)
 
 
 ---------------------------------------
 
 Small modification of htmlfilter.inc by  Konstantin Riabitsev and Jim Jagielski to address PHP 7.4 deprecation notices
 
# Problem

When using projects with phpmailer and php 7.4 you will receive a notices storm like this:

```
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 351
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 385
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 393
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 407
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 413
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 449
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 531
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 544
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 566
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 575
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 582
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 674
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 705
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 821
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 917
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 918
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 920
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 964
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 965
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 967
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1124
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1124
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1128
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1128
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1132
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1132
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1136
Deprecated: Array and string offset access syntax with curly braces is deprecated in PHPMailer/extras/htmlfilter.php on line 1136
```

Which is annoying to say the least when developing. Being distracted by all those notices.

And unfortunately you will find  a lot of live projects that will return that when you google any of that messages.

The worst: When PHP 8 arrives in less than 6 months (this is written on July 2020, and PHP is Expected to be released in December 2020) those **notices will become errors** turning your project's email functionality down.

This is just the replacing of `array{index}` to `array[index]` access in all those lines.

# Usage

Replace `htmlfilter.php`  in `PHPMailer/extras` folder with this file and you are done.

# Disclaimer
This is just the replacing of `array{index}` to `array[index]` access in all those lines. No further modifications were made and I still haven't noticed any side efects.
