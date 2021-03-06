# FinalizeBlock

Joke gem - This gem provide `finalize_block` method.
(or demonstration)

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'finalize_block'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install finalize_block

## Usage

You can use `finalize_block` method with a cleanup rule for a Class.
A rule is `a Class => Action Proc instance (action)` (now we support one pair of them).

All created objects (which are specified by a rule) in a block are passed to action proc at the end of block.
If created objects are freeed in a block, an action will not be called for freeed objects.

```
require 'finalize_block'

finalize_block String => -> str do
  # clear procedure by replacing with emtpy string.
  str.replace ''
end do
  $g = 'a' * 256     # create a String object
  p $g.size #=> 256  # 256B. Good.
end

p $g #=> '' # cleard at the end of block. Cool.
```

Note that this library is not tested and should be very buggy.

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/finalize_block.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
