## Basic Usage ##
The ics-Parser should only provide a very basic object to work with:

```
require 'class.iCalReader.php';

$ical = new ical('MyCal.ics');
print_r($ical->events());
```

## What does $ical->events() return? ##
```
Array
(
    [0] => Array
        (
            [DTSTART] => 20110105T090000Z
            [DTEND] => 20110107T173000Z
            [DTSTAMP] => 20110121T195741Z
            [UID] => 15lc1nvupht8dtfiptenljoiv4@google.com
            [CREATED] => 20110121T195616Z
            [DESCRIPTION] => This is a short description\nwith a new line. Some "special" 'signs' may be <interesting>\, too.
            [LAST-MODIFIED] => 20110121T195729Z
            [LOCATION] => Kansas
            [SEQUENCE] => 2
            [STATUS] => CONFIRMED
            [SUMMARY] => My Holidays
            [TRANSP] => TRANSPARENT
        )
 
    [1] => Array
        (
            [DTSTART] => 20110112
            [DTEND] => 20110116
            [DTSTAMP] => 20110121T195741Z
            [UID] => 1koigufm110c5hnq6ln57murd4@google.com
            [CREATED] => 20110119T142901Z
            [DESCRIPTION] => 
            [LAST-MODIFIED] => 20110119T152216Z
            [LOCATION] => 
            [SEQUENCE] => 2
            [STATUS] => CONFIRMED
            [SUMMARY] => test 11
            [TRANSP] => TRANSPARENT
        )
)
```

## How do I get a Unix timestamp out of a ical date? ##
If the date is before 1970, it returns false.

```
<?
require 'class.iCalReader.php';

$ical = new ical('MyCal.ics');
$array= $ical->events();

// The ical date
$date = $array[0]['DTSTART'];
echo $date;

// The Unix timestamp
echo $ical->iCalDateToUnixTimestamp($date);

?>
```

## How many events / todos are in the iCal? ##
```
<?
require 'class.iCalReader.php';

$ical = new ical('MyCal.ics');

// The number of events
echo $ical->event_count;

// The number of events
echo $ical->todo_count;

?>
```