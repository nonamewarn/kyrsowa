use std::env;
use std::fs::File;
use std::io::{self, BufRead, BufReader};
fn main() -&gt; io::Result&lt;()&gt; {
let args: Vec&lt;String&gt; = env::args().collect();
if args.len() &lt; 2 {
eprintln!(&quot;Використання: {} &lt;назва_файлу&gt;&quot;, args[0]);
return Ok(());
}
let filename = &amp;args[1];
let file = File::open(filename)?;
let reader = BufReader::new(file);
let count = reader.lines().count();
println!(&quot;Загальна кількість рядків у {}: {}&quot;, filename, count);
Ok(())
}
